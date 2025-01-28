# argparse

This repository contains a simple argument parser implementation in C. The parser supports parsing command-line options and positional arguments, providing a flexible framework for handling various types of inputs. I'm making this mainly to use for 42 Mastery projects where a lot of projects require parsing arguments.

## Features

- **Option Types**:
  - Flags (e.g., `-v`, `--verbose`)
  - Integer options (e.g., `-c 10`, `--count 10`)
  - String options (e.g., `-n John`, `--name John`)
- **Positional Arguments**:
  - Handles additional arguments not associated with options.
- **Usage Display**:
  - Displays all supported options.

## Getting Started

### Prerequisites

- GCC or any C compiler.
- Basic understanding of command-line argument parsing.

### Compilation

To compile the program, run the following command:

```bash
gcc -o argparse argparse.c
```

### Usage

Here is an example usage of the compiled program:

```bash
./argparse -v -c 5 -n "Example Name" arg1 arg2 arg3
```

### Example Output

```bash
Verbose: 1
Count: 5
Name: Example Name
Positional arguments:
  arg1
  arg2
  arg3
```

## Code Explanation

### Key Components

1. **Option Structure (`Option`)**:
   - Defines the flags, their types, and associated values.
2. **Argument Parser (`ArgParser`)**:
   - Manages the list of options and positional arguments.
3. **Initialization and Parsing Functions**:
   - `init_arg_parser`: Initializes the parser.
   - `add_option`: Adds a new option to the parser.
   - `parse_arguments`: Parses command-line arguments and assigns values to the appropriate variables.

### Adding Options

Use the `add_option` function to define options:

```c
add_option(&parser, "-v", "--verbose", ARGTYPE_FLAG, &verbose);
add_option(&parser, "-c", "--count", ARGTYPE_INT, &count);
add_option(&parser, "-n", "--name", ARGTYPE_STRING, &name);
```

- `-v` / `--verbose`: A flag option that sets `verbose` to `1` when provided.
- `-c` / `--count`: An integer option that assigns a value to `count`.
- `-n` / `--name`: A string option that assigns a value to `name`.

### Parsing Arguments

Call `parse_arguments` with `argc` and `argv`:

```c
parse_arguments(&parser, argc, argv);
```

This function matches provided arguments against the defined options and handles positional arguments.

### Displaying Usage

Use the `print_usage` function to display all supported options:

```c
print_usage(&parser);
```

## Limitations

- Maximum of 20 options and 20 positional arguments (can be adjusted by modifying `MAX_OPTIONS` and `MAX_POSITIONAL`).
- Does not support default values for options.
- No advanced error handling for malformed arguments.

## Contributing

Contributions are welcome! Feel free to open issues or submit pull requests to improve this project.

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

