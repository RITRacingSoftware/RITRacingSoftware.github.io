# Terminal
The terminal is a text-based way to interact with the files and programs on your computer.
It is used extensively here at RITRacing, because it is very quick to use, integrated, and highly configurable.
Here are some common terminal commands and a bit more about using it.

# Example repository
This will be the example repository layout used as examples for the commands described in this page:
```
new-project
├── src
│   ├── main
│   │   ├── main.c
│   │   └── main.h
│   └── driver
│       ├── driver.c
│       └── driver.h
├── scripts
│   ├── flash.sh
│   └── update_config.py
└── config.h
```

For all of the examples, expect to start in the `new-project` directory unless otherwise stated.

## Filepath notation
The notation for filepaths is standardized in the terminals we use.
- Your current directory is denoted with `./`
- The previous directory is denoted with `../`
- Your current directory is assumed to be the starting place for your filepaths: 
`./src/main/main.c` is treated the same as `src/main/main.c`.

The paths can be combined to express any file location in your system.

### Examples
- Relative to the `new-project` directory, `flash.sh` is located at `./scripts/flash.sh` or `scripts/flash.sh`
- If you are in the `scripts` directory, `main.c` is located at `../src/main/main.c`
- If you are in the `driver` directory, `flash.sh` is located at `../../scripts/flash.sh`

## ls (list)
This command will display all of the files in your current directory (folder).
It is run standalone, by running `ls` in your terminal.

### Examples
Running `ls` inside of the `new-project` repostory will yield
```bash
src scripts config.h
```
`src` and `scripts` are directories, `config.h` is a file.

## cd (change directory)
This command allows you to change the current directory you are in. It is run with the location to go to.

### Examples
- To navigate to the `scripts` directory from `new-project`, run `cd scripts`
- To navigate to the `main` directory from `scripts`, run `cd ../src/main`

*NOTE:* you can only `cd` into directories, you cannot `cd` into a file.


## sh/bash (run shell command)
This is the prefix needed to run some shell scripts on some systems.
A shell script is a collection of terminal commands that are run after you call the script. It is just a handy way
to bundle a common task that has multiple commands. Primarily, the scripts you will be running with this command will 
have the suffix `.sh` or `.bash`. Depending on the system, you may be able to run a script directly by typing the file's
name directly.

### Examples
- To run `flash.sh` from `new-project`, run `sh scripts/flash.sh` or `bash scripts/flash.sh` or `scripts/flash.sh`
