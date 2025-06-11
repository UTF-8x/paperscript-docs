# Usage

### The PaperScript CLI

```
USAGE:
    PaperScript.Cli.dll [OPTIONS] <COMMAND>

OPTIONS:
    -h, --help    Prints help information

COMMANDS:
    build        build a project (requires a project.yaml)
    transpile    transpiles a single file
    init         creates a new project.yaml
    version      prints version information
```

### init

Creates a new PaperScript project, sets up the directory structure and creates a `project.yaml` file in the current directory.

```
USAGE:
    paperscript init [OPTIONS]

OPTIONS:
    -h, --help     Prints help information
    -f, --force    Force creating a project in a non-dempty directory
```

### build

Builds a project in the current directory. Requires a valid `project.yaml` file.

```
USAGE:
    paperscript build [OPTIONS]

OPTIONS:
    -h, --help          Prints help information
    -n, --no-compile    do not run the papyrus compiler
```

### transpile

Transpiles a single file from PaperScript to Papyrus.

```
USAGE:
    paperscript transpile [INPUT FILE] [OPTIONS]

ARGUMENTS:
    [INPUT FILE]

OPTIONS:
    -h, --help                    Prints help information
    -o, --output <OUTPUT_FILE>
    -s, --stdout                  Output to STDOUT instead of a file
```

### version

Prints out version information for the CLI.

```
USAGE:
    paperscript version [OPTIONS]

OPTIONS:
    -h, --help    Prints help information
```
