# Minishell

**Minishell** is a simplified shell implementation written in C. It provides a minimalistic yet functional shell environment capable of executing commands, managing processes, and supporting built-in shell features.

## Table of Contents

- [Features](#features)
- [Directory Structure](#directory-structure)
- [Dependencies](#dependencies)
- [Installation](#installation)
- [Usage](#usage)
- [Makefile Targets](#makefile-targets)
- [Contributing](#contributing)
- [License](#license)

---

## Features

**Minishell** provides a streamlined shell environment with many core features found in Unix-like shells. Its capabilities include:

1. **Command Execution**: Execute binary commands by leveraging the `$PATH` environment variable, allowing users to run a wide range of programs directly from Minishell. Commands are launched in child processes, isolating each command’s environment and state.

2. **Built-in Commands**: Minishell includes core built-in commands, implemented internally to optimize performance and compatibility. These built-ins include:
   - `cd` (Change Directory): Allows the user to change the current working directory.
   - `echo` (Output Text): Prints text to the terminal, with options to suppress newlines.
   - `env` (Environment Variables): Displays all current environment variables.
   - `exit` (Exit Shell): Terminates the shell session with an optional exit code.
   - `export` (Set Environment Variables): Sets or updates environment variables for use in the shell.
   - `pwd` (Print Working Directory): Displays the path of the current directory.
   - `unset` (Unset Environment Variable): Removes environment variables.

3. **Environment Variable Management**: Supports creating, updating, and expanding environment variables, allowing flexibility in scripting and command execution. Variables can be referenced within commands using `$VAR` syntax, allowing dynamic configuration based on environment context.

4. **Logical Operators (`&&` and `||`)**: 
   - **AND (`&&`)**: Commands connected by `&&` are executed sequentially; the second command will only run if the first one succeeds.
   - **OR (`||`)**: Commands connected by `||` provide alternative execution paths; the second command runs only if the first one fails. 
   This logic enables users to create efficient and conditional command sequences directly in the shell.

5. **Pipelines and Redirections**:
   - **Pipes (`|`)**: Supports piping, allowing the output of one command to serve as the input for another, facilitating complex workflows.
   - **Redirections (`>`, `<`, `>>`)**: Provides file redirection, enabling users to send command output to files, read input from files, or append to files without overwriting content.

6. **Subshells and Parentheses for Command Prioritization**: Commands grouped in parentheses (`(...)`) run in subshells, allowing prioritized or isolated execution. This feature supports more complex command logic, letting users combine `&&`, `||`, and nested subshells to control execution flow precisely.

7. **Heredocs**: Supports "heredoc" input redirection (`<<`), allowing multi-line input to be redirected to a command. Heredocs provide a straightforward way to embed complex or multi-line input without using external files.

8. **Quoting and Expansion**:
   - **Quotes** (`'` and `"`): Supports single and double quotes to handle strings containing spaces or special characters.
   - **Variable Expansion**: Variables (e.g., `$VAR`) are expanded within commands, allowing dynamic values to be inserted.
   - **Wildcard Expansion**: Basic wildcard expansion is supported to match file and directory patterns in commands.

9. **Signal Handling**: Minishell responds gracefully to signals:
   - `Ctrl+C`: Interrupts the current command.
   - `Ctrl+D`: Sends an end-of-file (EOF) signal, allowing for shell exit in some contexts.
   - `Ctrl+\`: Handles the quit signal without causing unexpected exits.

10. **Error Handling**: Comprehensive error messages inform users of syntax errors, file issues, and other common problems, allowing for quick resolution. Graceful cleanup is performed to prevent memory leaks or lingering resources on errors.

11. **Syntax Parsing and Grammar Validation**: A robust parser interprets command syntax and builds an abstract syntax tree (AST) to ensure valid execution order and correct handling of nested commands. This component validates complex command patterns and sequences, supporting logical and arithmetic grouping, subshells, and prioritized command execution.

12. **Modular Design**: Minishell’s modular architecture divides functionality across components (parsing, execution, signal handling), making the codebase maintainable and extensible. This structure facilitates debugging, new feature implementation, and collaboration among developers.

---

## Directory Structure

```
minishell/
├── include/           # Header files
├── lib/               # External libraries
│   ├── libft/         # Libft library
│   └── printf/        # Custom printf implementation
├── objects/           # Build directory for compiled objects
├── src/               # Source files
│   ├── ast/           # Abstract syntax tree (AST) functionality
│   ├── builtins/      # Built-in shell commands
│   ├── envp/          # Environment variable handling
│   ├── error/         # Error handling and cleanup
│   ├── exec/          # Command execution
│   ├── grammar/       # Grammar and syntax validation
│   ├── heredoc/       # Heredoc input management
│   ├── parser/        # Parsing functionality
│   ├── principal/     # Main entry point and core logic
│   ├── signal/        # Signal management
│   ├── tokenizer/     # Tokenization and expansion
│   └── vector/        # Vector utilities
└── Makefile           # Build system
```

---

## Dependencies

- GCC or Clang
- `make` build system
- `readline` library for line editing support

---

## Installation

1. Clone the repository:
   ```bash
   git clone https://github.com/your-repository/minishell.git
   cd minishell
   ```

2. Build the project:
   ```bash
   make
   ```

---

## Usage

After building the project, run the shell with:
```bash
./minishell
```

Once launched, you can execute commands as you would in a standard shell.

Example:
```bash
minishell$ echo "Hello, World!"
Hello, World!
minishell$ export VAR=value
minishell$ echo $VAR
value
minishell$ exit
```

---

## Makefile Targets

| Target    | Description                                         |
|-----------|-----------------------------------------------------|
| `all`     | Default target, builds the project.                 |
| `libft`   | Compiles the `libft` library.                       |
| `printf`  | Compiles the `printf` library.                      |
| `clean`   | Removes all object files.                           |
| `fclean`  | Removes all built files and object files.           |
| `re`      | Cleans and rebuilds the project.                    |
| `norm`    | Runs `norminette` to check coding style compliance. |

