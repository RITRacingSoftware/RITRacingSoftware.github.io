# Terminal
The terminal is a text-based way to interact with the files and programs on your computer.
It is used extensively here at RITRacing, because it is very quick to use, integrated, and highly configurable.
Here are some common terminal commands and a bit more about using it. On MacOS and Linux, navigate to the `Terminal`
application and use that directly. For Windows, use the instructions in the main Firmware page to set up `WSL` and use 
that terminal to run commands.

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
- The parent directory is denoted with `../`
- Your current directory is assumed to be the starting place for your filepaths: 
`./src/main/main.c` is treated the same as `src/main/main.c`.

The paths can be combined to express any file location in your system.

### Examples
- Relative to the `new-project` directory, `flash.sh` is located at `./scripts/flash.sh` or `scripts/flash.sh`
- If you are in the `scripts` directory, `main.c` is located at `../src/main/main.c`
- If you are in the `driver` directory, `flash.sh` is located at `../../scripts/flash.sh`


## Tab Completion
When referencing a command or file on the command line, you can use the `tab` key to autocomplete your command.
If there are multiple valid files or directories that start with the text you wrote, it will display those as options.

### Examples
- To open `config.h` with `vim`, you can write `vim co<tab>`, and it will autofill to `vim config.h`
- If you run `cd s<tab>`, the terminal will display both `src` and `scripts`, as they are both valid options for your command.
If you wrote `cd sc<tab>` instead, it will autofill to `cd scripts` as it is the only valid option.


## Vim
Vim is a text editor that is built into the terminal. It makes for quick and seamless editing/viewing of files while inside the terminal.
While there are many advanced things that can be done with Vim, using it simply is quite easy. Vim is the recommended text editor
of the firmware team. Vim can be opened with the `vim <filename>` command. 

The idea of vim is that in different modes, the keys do different commands. The two main modes of Vim you will be using are 
Normal mode and Insert mode. In Normal mode, the keys will do special things, like navigating around the file.
In Insert mode, the keys will behave like a normal keyboard, and will insert directly into your document.
From Normal mode, enter Insert mode by pressing the `i` key. From Insert mode, enter normal mode by pressing the `esc` key.

### Common commands (all in Normal mode)
- Save the file with `:w`
- Quit the file with `:q`
- Quit the file without saving with `:q!`
- Search for text in your file with `/<text>`
- Jump to a line number with `:<line_number>`
- Jump to the end of a line and enter Insert mode with `shift + a`
- Copy a line with `yy`
- Paste with `p`

These are just very simple commands. Vim is an extremely powerful tool, and we encourage you to learn more about how to use it well.
There are many resources online for Vim motions and configuration.

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


## mkdir (make directory)
This makes a directory. Follow the command with the name of the directory you'd like to make

### Examples
- To make a directory named `new-directory` run `mkdir new-directory`
- To make a directory inside the `scripts` directory, run `mkdir scripts/new-directory`


## touch (make a new file)
This will create a new file with the name you enter following the `touch` command.

### Examples
- To make a file `notes.md` in `new-project`, run `touch notes.md`


