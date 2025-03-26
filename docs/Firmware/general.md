## Getting started
Users will generally have a directory on their system containing one copy of 
the Core, one copy of STM32G4 HAL, and one copy of the FreeRTOS kernel on 
their system. Each project they create will then use these libraries when 
compiling. It is recommended to have the following directory structure on
your system:
```
racing
├── core
├── Formula-DBC
├── FreeRTOS-Kernel
├── RTT
├── STM32CubeG4
├── <project1>
├── <project2>
└── <etc.>
```

Detailed instructions for setting up the core library and its dependencies
can be found in the [core documentation](https://rit-racing-core.readthedocs.io/en/latest/).


## Installing the required software
To compile code for an STM32 on your computer, a cross-compiler toolchain is
required. The preferred approach is to use the Docker image included in the
core library and the template project to compile your projects. The Docker
image already contains the required toolchain for compiling the code.

In addition to Docker, you will also need to install `git`. The procedure
for installing these packages varies by operating system. Finally, you will
need `openocd` on your system to flash the compiled binaries to the STM32.

### Linux
If `apt` is present on your distribution, `git` and `openocd` can be installed
with:
```bash
sudo apt install git openocd
```
For other distributions and installation options, see the official
documentation for [git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git)
and for [openocd](https://openocd.org/pages/getting-openocd.html). You can
also check your system's package manager for `git` and `openocd`.

On Linux, Docker can be installed by following the [official instructions](https://docs.docker.com/engine/install/ubuntu/#install-using-the-repository).
There are a number of ways of installing Docker on Linux, including via `apt`,
if it is installed on your system.

If you would like to save space on your computer or simplify the build process,
you also have the option of installing the cross-compilation toolchain directly
on your system:
```bash
sudo apt install gcc-arm-none-eabi gdb-multiarch
```
Then, all commands that you would normally run from the Docker shell can be run
directly from your terminal.

### MacOS


### Windows
OpenOCD: MSYS2?
Git: download installer
docker: ?

## Setting up a project
New projects are created from the [STM32G4xx-Template](https://github.com/RITRacingSoftware/STM32G4xx-Template)
remplate repository. Instructions for using the template can be found in the
template's README. When cloning the new project to your computer, it is
recommended that you clone it to the same directory that contains the core and
the HAL. If the project is stored in any other location, the Makefile will
need to be adjusted so the compiler can find the required libraries.

The instructions below will assume that you have `cd`'d into the project's
directory.

## Compiling a project
If you are using a docker image, you must first enter the docker image by
running `./scripts/enter-docker.sh` in a terminal. From there, run `make` to 
compile the project. From a second terminal window, run `./scripts/flash.sh`
to upload the compiled binary to the board via the J-Link programmer.

If you are not using a docker image, the `make` command can just be run from
the terminal directly.

## Debugging a project
There are several ways of debugging a program that is running on an STM32.
The simplest is to use the `rprintf` function to print to a terminal on your
computer. To use this function, you must include `rtt.h` in any file that
uses it. Then, to see the printed messages, run the following command in a
terminal window:
```bash
openocd -f rtt.cfg
```
This will start a server that you must connect to from another
terminal window by running the command:
```bash
nc localhost 8888
```
Any output from `rprintf` calls in the program will then be displayed in the
second terminal window

### Debugging with GDB
To use GDB to debug a program, start `openocd` as above:
```bash
openocd -f rtt.cfg
```
This will start a server that `gdb-multiarch` can connect to to debug the
program. If `gdb-multiarch` is installed directly on your system (rather than
in a docker image), then you can start the debugger by running `gdb-multiarch`
with the path to the executable as its argument. For example, if your project
is named `project1`, then the command is:
```bash
gdb-multiarch build/stm32/project1.elf
```
When this command is run, `gdb-multiarch` will run in interactive mode. Enter
the following command to attach the `gdb-multiarch` to the board
```
target extended-remote localhost:3333
```
[//]: https://gabriellesc.github.io/teaching/resources/GDB-cheat-sheet.pdf
You can then use standard GDB commands to inspect the state of the program and
the chip.
