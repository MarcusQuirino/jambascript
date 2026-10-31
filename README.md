# jambascript

A toy programming-language interpreter written in Go, built while working through
Thorsten Ball's book [*Writing an Interpreter in Go*](https://interpreterbook.com/).

## Status

Early stage: only the **lexer** and **token** definitions exist so far.

The lexer currently recognizes:

| Category                | Tokens                                   |
| ----------------------- | ---------------------------------------- |
| Keywords                | `fn`, `let`                              |
| Identifiers & literals  | identifiers (letters and `_`), integers  |
| Operators               | `=`, `+`                                 |
| Delimiters              | `,` `;` `(` `)` `{` `}`                  |
| Special                 | `ILLEGAL`, `EOF`                         |

Whitespace (spaces, tabs, `\n`, `\r`) is skipped. Example input the lexer handles:

```
let add = fn(x, y) {
  x + y;
};

let result = add(five, ten);
```

## Roadmap

- [x] Lexer (basic token set above)
- [ ] Extended tokens (`-`, `!`, `*`, `/`, `<`, `>`, `==`, `!=`, `if`/`else`/`return`/`true`/`false`)
- [ ] Parser (AST, Pratt parsing)
- [ ] Evaluator
- [ ] REPL

## Project layout

The repo is a Go workspace (`go.work`, Go 1.21.6) with one module per package:

```
go.work          # uses ./lexer and ./token
lexer/           # module MarcusQuirino/lexer
token/           # module MarcusQuirino/token
```

## Running the tests

Requires Go 1.21.6+. Run from the `lexer` directory so the workspace resolves the
`MarcusQuirino/token` import:

```sh
cd lexer
go test ./...
```
