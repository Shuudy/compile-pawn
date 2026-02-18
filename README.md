# Pawn Compile Action

A GitHub Action to effortlessly download the [Zeex Pawn compiler](https://github.com/pawn-lang/compiler) and compile any Pawn (`.pwn`) source files directly in your CI/CD workflows.

This action allows you to automate the compilation process, catch syntax errors, and review the compiler output for any SA:MP or open.mp project (gamemodes, filterscripts, and standalone scripts).

## Inputs

This action supports the following inputs:

| Input          | Description                                                                                                                           | Required | Default         |
| -------------- | ------------------------------------------------------------------------------------------------------------------------------------- | -------- | --------------- |
| `source`       | Path to the `.pwn` file to compile                                                                                                    | `true`   | -               |
| `include-path` | Path to the directory containing your `.inc` files.                                                                                   | `false`  | `pawno/include` |
| `version`      | The specific Zeex Pawn compiler version to use.                                                                                       | `false`  | `3.10.10`       |
| `args`         | Additional arguments to pass to the compiler. See the [detailed list of options](https://github.com/pawn-lang/compiler/wiki/Options). | `false`  | -               |

## Usage

```yaml
# .github/workflows/compile.yml

name: Compile Pawn Script

on:
  push:
    branches:
      - main

jobs:
  compile:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout repository
        uses: actions/checkout@v4

      - name: Compile a Gamemode
        uses: Shuudy/compile-pawn@v1
        with:
          source: 'gamemodes/mygamemode.pwn'
          include-path: 'pawno/include'
          args: '-d3'
```

## Contributing

Contributions, issues, and feature requests are welcome!

## License

This project is licensed under the [MIT License](LICENSE).
