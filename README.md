# Task 1: Environment Setup & RISC-V Reference Bring-Up 


## 1. Experimental Logs & Execution Proof

###  Reference Program Setup
The development environment was successfully initialized within a containerized GitHub Codespace. The core software repository structure was verified, and the primary test script `sum1ton.c` was located within the local environment path.

#### Command used to navigate to the reference files directory
cd /workspaces/Task-1/samples
ls -ltr

<img width="478" height="237" alt="Screenshot 2026-06-23 121120" src="https://github.com/user-attachments/assets/a4a4e82e-cc47-4e19-923a-25077d6ab994" />

### Spike Simulation Output
The C program was cross-compiled using the RISC-V GNU toolchain framework to generate an execution object file compatible with the RISC-V architecture. This binary file was then functionally validated and emulated on the Spike ISA Simulator running alongside the standard Proxy Kernel (pk) wrapper.


#### Compilation Command
riscv64-unknown-elf-gcc -o sum1ton.o sum1ton.c

#### Execution Command using the Spike ISA Simulator
spike pk sum1ton.o

<img width="1003" height="117" alt="Screenshot 2026-06-22 191139" src="https://github.com/user-attachments/assets/77b0f575-544f-416b-8309-941ba25cb0e1" />

<img width="927" height="405" alt="Screenshot 2026-06-22 191053" src="https://github.com/user-attachments/assets/e5d4fd06-186e-484d-8be0-6f17fd372d94" />

### Modified Program
To verify the dynamic linking, recalculation capacity, and behavior of the underlying compilation framework, the upper boundary condition variable loop limit n was customized inside the source code text block using the local text terminal editor.

<img width="443" height="237" alt="Screenshot 2026-06-23 121105" src="https://github.com/user-attachments/assets/1d558191-c008-40bd-a893-98d7bd76410d" />

#### Command used to open and review modifications in the source file
cat sum1ton.c
### Modified Program Output
The updated source file was re-compiled and evaluated through the functional simulation channel to ensure that the core calculations updated accurately according to the configuration adjustments.



#### Re-compiling the updated code structure
riscv64-unknown-elf-gcc -o sum1ton.o sum1ton.c

#### Re-running the simulation loop
spike pk sum1ton.o

<img width="958" height="90" alt="Screenshot 2026-06-23 103441" src="https://github.com/user-attachments/assets/62e659dd-c5a0-438e-a0eb-e26b70c4d11c" />

## 2. VSDFPGA Lab
### Firmware 
The underlying software framework for the VSDFPGA design lab was cloned successfully.
#### Navigating to the Firmware target path
cd /workspaces/Task-1/vsdfpga_labs/basicRISCV/Firmware

<img width="1522" height="552" alt="Screenshot 2026-06-23 121942" src="https://github.com/user-attachments/assets/7776cfd8-4985-42c8-aad2-0f3ebc20c18b" />


## Mandatory Understanding Check
##### Q1: Where is the RISC-V program located in the vsd-riscv2 repository?
 The reference RISC-V program is located in the samples directory. An example program used during this task is:

samples/sum1ton.c
##### Q2: How is the program compiled and loaded into memory?
The C program is compiled using the RISC-V cross compiler:
       riscv64-unknown-elf-gcc -o sum1ton.o sum1ton.c

The generated executable is then loaded and executed by the Spike ISA Simulator using the Proxy Kernel (pk):
       spike pk sum1ton.o

##### Q3: How does the RISC-V core access memory and memory-mapped IO?
The RISC-V core accesses memory and peripherals through load and store instructions. Memory-mapped IO devices are assigned specific address ranges. The processor communicates with peripherals by reading from and writing to those mapped addresses.

##### Q4: Where would a new FPGA IP block logically integrate in this system?
A new FPGA IP block would typically be connected as a memory-mapped peripheral on the system bus. The RISC-V processor can then access the IP through dedicated address locations using standard load and store operations.

## Environment Confirmation Statement
System Environment Profile: GitHub Codespace Only 
