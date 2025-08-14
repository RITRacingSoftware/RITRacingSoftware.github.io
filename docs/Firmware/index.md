<style>
    ol li {
        padding-bottom: 0px;
        line-height: 1.6;
    }
</style>
## Getting started
Users will generally have a directory on their system containing one copy of 
the Core, one copy of STM32G4 HAL, and one copy of the FreeRTOS kernel on 
their system. Each project they create will then use these libraries when 
compiling. It is recommended to have the following directory structure on
your system:
```
RITRacing
├── core
├── Formula-DBC
├── FreeRTOS-Kernel
├── RTT
├── STM32CubeG4
├── <project1>
├── <project2>
└── <etc.>
```
Where precisely this folder will be located will depend on your system and
personal preferences.

## Installing the prerequisites
To compile code for an STM32 on your computer, a cross-compiler toolchain is
required. On Linux, the required packages can be installed directly to your
system or in a Docker image. On MacOS, the required packages can be installed 
directly to your system via Homebrew. On Windows, the toolchain is installed with
Windows Subsystem for Linux.

You will also need to install `git` for accessing our Github repositories
and `openocd` for flashing compiled binaries to the STM32. The exact process
for installing these varies by operating system.

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

Similarly, the cross-compilation toolchain can be installed with:
```bash
sudo apt install gcc-arm-none-eabi gdb-multiarch
```

The `RITRacing` directory containing the prerequisite libraries and code can be
placed anywhere on your system. To set up the core library and its
dependencies, see [the core library docs](https://rit-racing-core.readthedocs.io/en/latest/).

### MacOS
To begin, you will need to install Homebrew, a package manager for MacOS. You can follow the
instructions on their [website](https://brew.sh/), or you can paste the following command in your terminal:
```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```
Once Homebrew is installed, you can begin to use it to install the necessary packages.

Install the GCC embedded toolchain with:
```bash
brew install --cask gcc-arm-embedded
```

Then, install `openocd` with:
```bash
brew install open-ocd
```

If `git` isn't present on your system already, it can be installed with:
```bash
brew install git
```

Next, the core library and its dependencies need to be installed, if not already. The instructions
for that can be found in [the core library docs](https://rit-racing-core.readthedocs.io/en/latest/).
The correct foler structuring can be found at the top of this page, or in the core documentation.

### Windows
To install the required software, you will need to install Windows Subsystem
for Linux. You will not need Docker on Windows. 

Press the Windows key and search for "Turn Windows features on or off". Make 
sure that the following options are turned on:

 - Virtual Machine Platform
 - Windows Hypervisor Platform
 - Windows Subsystem for Linux

Then, open Windows PowerShell and enter:
```
wsl --install
```
If a reboot is required, reboot your computer now. After rebooting, open
PowerShell and run:
```
wsl --install -d Ubuntu-22.04
```
You will be asked to set up a user with a password. Once you have created
the user, you should be on the Linux terminal. If not, run `wsl` to enter.
Run the following to install the required packages:
```
sudo apt update
sudo apt install git make gcc-arm-none-eabi gdb-multiarch openocd
```

The `RITRacing` directory containing the prerequisite libraries and code can be
placed anywhere within the WSL filesystem. To set up the core library and its
dependencies, see [the core library docs](https://rit-racing-core.readthedocs.io/en/latest/).


## Setting up a project
New projects are created from the [STM32G4xx-Template](https://github.com/RITRacingSoftware/STM32G4xx-Template)
remplate repository. Instructions for using the template can be found in the
template's README. When cloning the new project to your computer, you should
clone it to the same directory that contains the core and the HAL. If the 
project is stored in any other location, the Makefile will need to be adjusted
so the compiler can find the required libraries.

Alternatively, an existing project can be gloned from Github. For example, to
clone the `core-vc` project, use the following command:
```bash
git clone git@github.com:RITRacingSoftware/core-vc.git
```

The instructions below will assume that you have `cd`'d into the project's
directory.

## Compiling a project
If you are using a docker image, you must first enter the docker image by
running `./scripts/enter-docker.sh` in a terminal. From there, run `make` to 
compile the project.

If you are not using a docker image, the `make` command can just be run from
the terminal directly.

## Flashing a project
Compiled binaries are typically flashed in one of two ways. During development,
this is most commonly done with a J-link programmer, which connects to your
computer via USB. For boards in the car, this is typically done via MCan. In
both cases, this can be done by running the script `./scripts/flash.sh`, which
is located in the project repository. This script does four things:

 1. The script looks in the Makefile and determines the filename of the 
    compiled binary.
 2. The script tries to connect to an existing instance of `openocd` with
    `telnet`. If this is possible, it commands `openocd` to upload the binary
    and exits. This feature is useful if you are debugging a project with
    RTT (as explained below) and you would like to upload without stopping
    your RTT session.
 3. Next, it tries to connect to MCan. If this is possible, the binary is
    uploaded with MCan and the script exits.
 4. Finally, the script invokes `openocd` to upload the binary.

### USB passthrough
On Windows, a few additional steps are required to allow the J-link to be
accessed by programs within WSL:

 1. Open a Windows PowerShell as administrator and install `usbipd` with 
    `winget install --interactive --exact dorssel.usbipd-win`
 2. Follow the prompts to install `usbipd`. Once the installation has 
    completed, close and reopen the PowerShell, again as administrator. 
 3. Plug J-link into your computer
 4. Run `usbsetup.cmd` in the `scripts` directory. You will have to re-run
    this step every time the J-link is plugged in.

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
second terminal window.

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
You can then use standard GDB commands to inspect the state of the program and
the chip. See [this document](https://gabriellesc.github.io/teaching/resources/GDB-cheat-sheet.pdf)
for an overview of GDB commands.
