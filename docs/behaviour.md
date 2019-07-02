# Parser Behaviour

The following set of behaviours are replicated by the output of **all** valid argspec argument parsers.

## Convention

The following convention will be used.

- `prog` is a command-line program
- `-x`, `-y` and `-z` are arguments to `prog`; each of `-x`, `-y` and `-z` is a flag
- `--str` is an argument to `prog` and has type `string`
- `--chr` is an argument to `prog` and has type `char`
- `--num` is an argument to `prog` and has type `int`
- `--bl` is an argument to `prog` and has type `bool`
- `--hlp` is an argument to `prog` and has type `help`

## Types

Argspec specifies several types of arguments.
In a valid (i.e. non-malformed) call, the following hold.

1. The call is of the form

    ```bash
    prog [arguments...]
    ```

    where `[arguments...]` has the following properties
2. If `-x` is a flag, then `-x` can be present as a word in `[arguments...]`.
   It's value is _true_ if `-x` is present.
3. If `--str` is a string argument, then it must be followed by exactly one string to capture
4. If `--chr` is a character argument, then it must be followed by a string of length one
5. If `--bl` is a boolean argument, then it must be followed by either `true` or `false` (case-sensitive)
6. If `--num` is an integer argument, then it must be followed by a non-zero number of digits 0–9
7. If `--hlp` is a help-argument, then it may be present in any place as a ` argument

Multiple _flag_ arguments may be concatenated after a single dash.
For example, if `-xyz` is seen, this is treated equivalently to having seen `-x -y -z`.
**This behaviour does not extend to other types.**

## Behaviour

An valid argument parser has a method named `parseArgs`.
This must take a list of strings and return a `struct`/object-like value which contains the arguments.
This operates as follows.

### Under Normal conditions

For each argument, the name of the field where the associated argument is given by the `dest` field in the JSON specification.

### Under Malformed Conditions

When a malformed argument string is presented, the parser does the following.

1. It outputs a synopsis of the command generated from its arguments
    - Short forms are preferred here
    - Where an argument takes another value, this is replaced by the value in the `metadest` field of the schema.
2. It outputs the string which caused the error (e.g. `--some-unrecognised-argument`)
3. It exits with code 1
