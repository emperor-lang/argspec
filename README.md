# argspec

This is an argument specification schema, designed to specify a verifiable contract with users of programs.
It allows a programmer to specify clearly exactly how their program will interact with the system in a way which is easy to maintain.

It currently has two main purposes─these are as follows

1. To allow documentation to be more easily generated (e.g. `man`-pages without requiring knowledge of `*roff` syntax)
2. To allow argument parsers to be generated from the specified data which adhere to the specification

These are detailed in the following sections.

## Generating Documentation

JSON specifications which adhere to `argspec`, form a unified way of generating documentation on a variety of platforms.
Two currently supported are:

- Linux man pages (example: [mangen](https://github.com/arggen/mangen))
- Web-based documentation (example [ManualHTML](https://github.com/jf908/ManualHTML))

## Generating Parsers

Parser-generators which take `argspec` JSON specifications may be used to generate up-to-date, modular parsers for command-line arguments.
Known examples are:

- [`arggen_c`](https://github.com/argspec/arggen)
- [`arggen_haskell`](https://github.com/argspec/arggen)
- [`arggen_python`](https://github.com/argspec/arggen)

A behaviour-specification for parsers produced from valid argspec parser generators can be found in [behaviour.md](./docs/behaviour.md)
