# Software

The [software directory](https://github.com/phoeniX-Digital-Design/phoeniX/blob/main/Software) contains source files for the assembler, sample codes, and user codes which can be executed on the phoeniX core.

- Download V0.4.1 [[zip](https://github.com/phoeniX-Digital-Design/phoeniX/archive/refs/tags/V0.4.1.zip)] [[tar.gz](https://github.com/phoeniX-Digital-Design/phoeniX/archive/refs/tags/V0.4.1.tar.gz)]
- Download V0.4.0 [[zip](https://github.com/phoeniX-Digital-Design/phoeniX/archive/refs/tags/V0.4.zip)] [[tar.gz](https://github.com/phoeniX-Digital-Design/phoeniX/archive/refs/tags/V0.4.tar.gz)]
- Download V0.3.0 [[zip](https://github.com/phoeniX-Digital-Design/phoeniX/archive/refs/tags/V0.3.zip)] [[tar.gz](https://github.com/phoeniX-Digital-Design/phoeniX/archive/refs/tags/V0.3.tar.gz)]
- Download V0.2.0 [[zip](https://github.com/phoeniX-Digital-Design/phoeniX/archive/refs/tags/V0.2.zip)] [[tar.gz](https://github.com/phoeniX-Digital-Design/phoeniX/archive/refs/tags/V0.2.tar.gz)]
- Download V0.1.0 [[zip](https://github.com/phoeniX-Digital-Design/phoeniX/archive/refs/tags/V0.1.zip)] [[tar.gz](https://github.com/phoeniX-Digital-Design/phoeniX/archive/refs/tags/V0.1.tar.gz)]

## Building RISC-V Toolchain
 
In order to be able to compile your source files and run on the core, you need to install `RISC-V GNU Compiler Toolchain`. You can follow the installation process from the [riscv-gnu-toolchain](https://github.com/riscv-collab/riscv-gnu-toolchain) repository or use the scripts provided in the original RISC-V repositories and [riscv-tools](https://github.com/riscv/riscv-tools). The default settings in the original repos build scripts will build a compiler, assembler and linker that can target any RISC-V ISA.

You can also use the provided shell script in `/Setup` directory. All shell scripts and Makefiles provided in this repository target `Ubuntu 20.04` unless otherwise specified. Simply run the `setup.sh` from your terminal, and it will automatically install all required prequistes.


```sh
user@Ubuntu:~$ git clone https://github.com/phoeniX-Digital-Design/phoeniX.git
user@Ubuntu:~$ cd phoeniX
user@Ubuntu:~$ cd Setup
user@Ubuntu:~$ chmod +x setup.sh
user@Ubuntu:~$ ./setup.sh
```

Using your favorite editor open `.bashrc` file from the `home` directory of your ubuntu. Replace `{user}` with your own user name and add the following lines to the end of file. This will change your path environment variable and is required to run `RISC-V GNU Compiler` automatically without exporting `PATH` variable each time.


> The script provided `setup.sh` and the following lines are set configure the toolchain based on `8.3.0` version of the compiler and toolchain for a `x86_64` machine. If you wish to install a different version please beware and change the required lines in `setup.sh` and the following lines.

```sh
export PATH=/home/{user}/riscv_toolchain/riscv64-unknown-elf-gcc-8.3.0-2019.08.0-x86_64-linux-ubuntu14/bin:$PATH
export PATH=/home/{user}/riscv_toolchain/riscv64-unknown-elf-gcc-8.3.0-2019.08.0-x86_64-linux-ubuntu14/riscv64-unknown-elf/bin:$PATH
```

## AssembleX V3.0

The [`AssembleX`](https://github.com/phoeniX-Digital-Design/AssembleX) software is an assembly code executant designed for the [phoeniX](https://github.com/phoeniX-Digital-Design/phoeniX) project. Version 3.0 supports `RV32IM` extenstions of standard RISC-V ISA.

- Download V3.0 [[zip](https://github.com/phoeniX-Digital-Design/AssembleX/archive/refs/tags/AssembleX-V3.0.zip)] [[tar.gz](https://github.com/phoeniX-Digital-Design/AssembleX/archive/refs/tags/AssembleX-V3.0.tar.gz)]


### Running Sample Codes

To run any of these sample projects simply run python `AssembleX.py sample` followed by the name of the project passed as a variable named project to the Python script.
The input command format for the terminal follows the structure illustrated below:
```shell
python AssembleX.py sample {project_name}
```
For example:
```shell
python AssembleX.py sample fibonacci
```
After execution of this script, firmware file will be generated and this final file can be directly fed to our Verilog testbench. AssembleX automatically runs the testbench and calls upon gtkwave to display the selected signals in the waveform viewer application, gtkwave.

### Running Your Own Code

In order to run your own code on phoeniX, create a directory named to your project such as `/my_project` in `/Software/User_Codes`. Put all your `user_code.s` files in my_project and run the following command from the main directory:

```shell
python AssembleX.py code my_project
```

Provided that you name your project sub-directory correctly the AssembleX software will create `my_project_firmware.hex` and fed it directly to the testbench of phoeniX processor. After that, iverilog and GTKWave are used to compile the design and view the selected waveforms.


## RISC-V GCC-GNU Compiler Toolchain

### Running Sample Codes

The directory `/Software` contains sample codes for some conventional programs and algorithms in both Assembly and C which can be found in `/Sample_Assembly_Codes` and `/Sample_C_Codes` sub-directories respectively. 

phoeniX convention for naming projects is as follows; The main source file of the project is named as `{project.c}` or `{project.s}`. This file along other required source files are kept in one directory which has the same name as the project itself, i.e. `/project`.

Sample projects provided at this time are `bubble_sort`, `fibonacci`, `find_max_array`, `sum1ton`.
To run any of these sample projects simply run `make sample` followed by the name of the project passed as a variable named project to the Makefile.
```shell
make sample project={project}
```
For example:
```shell
make sample project=fibonacci
```

Provided that the RISC-V toolchain is set up correctly, the Makefile will compile the source codes separately, then using the linker script `riscv.ld` provided in `/Firmware` it links all the object files necessary together and creates `firmware.elf`. It then creates `start.elf` which is built from `start.s` and `start.ld` and concatenate these together and finally forms the `{project}_firmware.hex`. This final file can be directly fed to our verilog testbench. Makefile automatically runs the testbench and calls upon `gtkwave` to display the selected signals in the waveform viewer.


### Running Your Own Code

In order to run your own code on phoeniX, create a directory named to your project such as `/my_project` in `/Software/User_Codes/`. Put all your `.c` and `.s` files in `/my_project` and run the following `make` command from the main directory:
```shell
make code project=my_project
```
Provided that you name your project sub-directory correctly and the RISC-V Toolchain is configured without any troubles on your machine, the Makefile will compile all your source files separately, then using the linker script `riscv.ld` provided in `/Firmware` it links all the object files necessary together and creates `firmware.elf`. It then creates `start.elf` which is built from `start.s` and `start.ld` and concatenate these together and finally forms the `my_project_firmware.hex`. After that, `iverilog` and `gtkwave` are used to compile the design and view the selected waveforms.

> Further Configurations: The default testbench provided as `phoeniX_Testbench.v` is currently set to support up to 4MBytes of memory and the stack pointer register `sp` is configured accordingly. If you wish to change this, you need configure both the testbench and the initial value the `sp` is set to in `/Firmware/start.s`. If you wish to use other specific libraries and header files not provided in `/Firmware` please beware you may need to change linker scripts `riscv.ld` and `start.ld`.

[Back to Homepage.](https://phoenix-digital-design.github.io/)