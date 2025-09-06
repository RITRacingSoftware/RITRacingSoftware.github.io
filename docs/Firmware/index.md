<style>
    ol li {
        padding-bottom: 0px;
        line-height: 1.6;
    }

    r { color: Red }
    b { color: Blue }
    o { color: Orange }
    g { color: Green }
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

## Coding Style
There is no official "style guide" for RITRacing. However, you do have to set your tabs to 4 spaces.

## Navigation
All of our installation and compilation will be done with terminal commands. The terminal is just another
way to navigate your computer's file system and interact with the programs and files you have. If you're not
already comfortable using the terminal you should review the [Terminal](./Terminal.md) page.

## Installing the prerequisites
To compile code for an STM32 on your computer, a cross-compiler toolchain is
required. On Linux, the required packages can be installed directly to your
system or in a Docker image. On MacOS, the required packages can be installed 
directly to your system via Homebrew. On Windows, the toolchain is installed with
Windows Subsystem for Linux.

By the end of this you should have:

- Via pacakage manager:
    - openocd
    - git
    - make
    - gcc-arm-none-eabi (Windows/Linux)
    - gcc-arm-embedded (MacOS)
    - gdb-multiarch (optional)
- Via GitHub:
    - [core](https://github.com/RITRacingSoftware/core)
    - [Formula-DBC](https://github.com/RITRacingSoftware/Formula-DBC)
    - [STM32CubeG4](https://github.com/STMicroelectronics/STM32CubeG4)
    - [FreeRTOS-Kernel](https://github.com/FreeRTOS/FreeRTOS-Kernel)
    - [RTT](https://github.com/SEGGERMicro/RTT)

First, we will install the external dependencies handled by a package manager.
This will vary depending on your system.


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
Some features of our flash script will require `telnet` as well.


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

Check to see if `git` is installed on your system with `git --version`.
If `git` isn't present on your system already, it can be installed with:
```bash
brew install git
```

Check to see if `make` is installed on your system with `make --version`.
If `make` isn't present on your system already, it can be installed with:
```bash
brew install make
```


### Windows
To install the required software, you will need to install Windows Subsystem
for Linux. You will not need Docker on Windows. 

Press the Windows key and search for "Turn Windows features on or off". Make 
sure that the following options are turned on:

 - Virtual Machine Platform
 - Windows Hypervisor Platform
 - Windows Subsystem for Linux

You will need to run commands both in <r> Windows Powershell </r> and in <g> WSL </g>.
They will be denoted in this color coding.

<r> In Windows Powershell, run: </r>
```
wsl --install
```

If a reboot is required, reboot your computer now.

<r> After the reboot, in Windows Powershell run: </r>
```
wsl --install -d Ubuntu-22.04
```

You will be asked to set up a user with a password. Once you have created
the user, you should be on the Linux terminal.

<r> If not, in Windows Powershell enter WSL by running: </r>
```
wsl
```

<g> In WSL, install packages by running: </g>
```
sudo apt update
sudo apt install git make gcc-arm-none-eabi gdb-multiarch openocd usbutils telnet
```

### GitHub dependencies
The `RITRacing` directory containing the prerequisite libraries and code can be
placed anywhere within the WSL filesystem, but place them all in the RITRacing directory.
The following commands can be run on any OS, but if you are using Windows make sure to use WSL.

#### External dependencies
These repositories weren't written by us, but are necessary for compilation.

Install the [STM32CubeG4](https://github.com/STMicroelectronics/STM32CubeG4) repository with:
```bash
git clone --recursive https://github.com/STMicroelectronics/STM32CubeG4.git
```
Install the [FreeRTOS-Kernel](https://github.com/FreeRTOS/FreeRTOS-Kernel) repository with:
```bash
git clone --recursive https://github.com/FreeRTOS/FreeRTOS-Kernel.git
```
Install the [RTT](https://github.com/SEGGERMicro/RTT) repository with:
```bash
git clone https://github.com/SEGGERMicro/RTT.git
```

#### Internal dependencies
These repositories have been written by us:

Install the [core](https://github.com/RITRacingSoftware/core) repository with:
```bash
git clone https://github.com/RITRacingSoftware/core.git
```
Install the [Formula-DBC](https://github.com/RITRacingSoftware/Formula-DBC) repository with:
```bash
git clone https://github.com/RITRacingSoftware/Formula-DBC.git
```

To configure the core library within your project, check out [the core library docs](https://rit-racing-core.readthedocs.io/en/latest/)


## Setting up a project
New projects are created from the [STM32G4xx-Template](https://github.com/RITRacingSoftware/STM32G4xx-Template)
template repository. Instructions for using the template can be found in the
template's README. When cloning the new project to your computer, you should
clone it to the same directory that contains the core and the HAL. If the 
project is stored in any other location, the Makefile will need to be adjusted
so the compiler can find the required libraries.

For simple test code for the new member project, clone the [STM32G4xx-Template](https://github.com/RITRacingSoftware/STM32G4xx-Template)
repository with:
```bash
git clone https://github.com/RITRacingSoftware/STM32G4xx-Template.git
```
You can edit the code inside the template without creating another repository from it, 
and it will have everything you need to get started.


Alternatively, an existing project can be cloned from Github. For example, to
clone the `core-vc` project, use the following command:
```bash
git clone https://github.com/RITRacingSoftware/core-vc.git
```

The instructions below will assume that you have `cd`'d into the project's
directory.

## Compiling a project
To compile a project, run the `make` command from the terminal. This command
will generate a `.elf` binary image and a `.ihex` file.

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
accessed by programs within WSL.
All of the following commands should be run in <r> Windows Powershell, opened as an administrator </r>.

 1. <r> Run </r> `winget install --interactive --exact dorssel.usbipd-win` to install `usbipd`.
 2. Follow the prompts to install `usbipd`. Once the installation has 
    completed, close and reopen the PowerShell, again as administrator.
 3. Plug J-link into your computer
 4. <r> Run </r> `usbsetup.cmd` in the `scripts` directory. You will have to re-run
    this step every time the J-link is plugged in.

### USB passthrough alternative
In the event that step 4 in the above list didn't work, the USB can be connected to WSL manually.
Run the following steps instead of step 4, you do not need to repeat steps 1-3.

 1. <r> In Windows Powershell run </r> `usbipd list`. Note the `BUSID` of the device `J-Link`.
 2. <r> Run </r> `usbipd bind --busid <busid>`, replacing `<busid>` with the ID of your J-Link recorded in step 1.
 3. <r> Run </r> `usbipd attach --wsl --busid <busid>`.
 4. <g> In WSL, run </g> `lsusb`, and confirm the J-Link is attached.
 
 You can now flash by <g> running </g> `./scripts/flash.sh` in <g> WSL </g> from your parent project directory.

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
