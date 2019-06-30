# argspec

This is an argument specification schema, designed to specify a verifiable contract with users of programs.
It allows a programmer to specify clearly exactly how their program will interact with the system in a way which is easy to maintain.

It currently has three main purposes─these are as follows

1. To allow documentation to be more easily generated (e.g. `man`-pages without requiring knowledge of `*roff` syntax)
2. To allow argument parsers to be generated from the specified data which adhere to the specification
3. To allow tests to be generated to verify that the schema is correct

These are detailed in the following sections.

## Generating Documentation

JSON specifications which adhere to `argspec`, form a unified way of generating documentation on a variety of platforms.
Two currently supported are:

- Linux man pages (example: [mangen](https://github.com/emperor-lang/mangen))
- Web-based documentation

## Generating Parsers

Parser-generators which take `argspec` JSON specifications may be used to generate up-to-date, modular parsers for command-line arguments.
Known examples are:

- [`arggen-c`](https://github.com/emperor-lang/arggen)
- [`arggen-haskell`](https://github.com/emperor-lang/arggen)
- [`arggen-python`](https://github.com/emperor-lang/arggen)

## Testing

Automatic tests may be generated from the specification.
Current (known) programs which do this:

- [`testgen`](https://github.com/emperor-lang/testgen)
