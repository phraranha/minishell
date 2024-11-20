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

- **Command Execution**: Execute binary commands found in `$PATH`.
- **Built-in Commands**: Includes essential shell built-ins like `cd`, `echo`, `env`, `exit`, `export`, `pwd`, and `unset`.
- **Environment Variable Management**: Support for environment variable expansion and manipulation.
- **Pipelines and Redirections**: Implements basic pipe (`|`) and redirection (`>`, `<`) functionalities.
- **Heredocs**: Support for heredoc (`<<`) input redirection.
- **Signal Handling**: Proper handling of signals such as `Ctrl+C`, `Ctrl+D`, and `Ctrl+\`.
- **Error Handling**: Graceful error messages and cleanup on invalid input or system errors.

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

