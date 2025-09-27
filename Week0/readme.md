# <p align="center">💻RISC-V REFERENCE SOC TAPOUT PROGRAM
</p>


### 📚Contents

 - [Task 1: Welcomw Call](https://github.com/VIJAYAKUMARAHS/RISC-V_SOC_Tapeout_Program/edit/main/Week0/readme.md#task-1-welcome-call)

 - [Task 2: Tools Installation](https://github.com/VIJAYAKUMARAHS/RISC-V_SOC_Tapeout_Program/tree/main/Week0#task-2-tools-installation)

# 🚀Task 1: Welcome Call

## 📔 Here I am going to document the Welcome call of the RISC-V SOC Tapeout Program!

<p align="center">
<img width="600" height="400" alt="Welcome poster" src="https://github.com/user-attachments/assets/91f49b16-3b68-47ab-8671-dbaf7cef9713" />
</p>

### Agenda

<p align="center">
<img width="600" height="400" alt="image" src="https://github.com/user-attachments/assets/b14b226f-9a4c-43f6-9c69-9387cbd858f5" />
</p>

### Why this Lab?

<p align="center">
<img width="600" height="400" alt="image" src="https://github.com/user-attachments/assets/db27ee82-b615-439e-bbf7-f60f44adabf5" />
</p>

### Phasewise Learning Path

<p align="center">
<img width="600" height="400" alt="image" src="https://github.com/user-attachments/assets/a0ff319e-4442-4beb-8e2f-492f3ba61241" />
</p>

### Destination

<p align="center">
<img width="600" height="400" alt="image" src="https://github.com/user-attachments/assets/fc798530-e600-4362-9cf0-df56f1e651a8" />
</p>

### Week-Wise Task

<p align="center">
<img width="600" height="400" alt="image" src="https://github.com/user-attachments/assets/1aab9be8-3d24-4c11-926e-86372ea0d6ab" />
</p>

### Keynote Addressed by

Dr. Rajat Mooba, Director, IIT Gandhinagar.

<p align="center">
<img width="600" height="400" alt="image" src="https://github.com/user-attachments/assets/8da1711c-5413-4db9-9145-d26b6004fba7" />
</p>

### Expert Insights

Mr. Samir Patel, Visiting Faculty,  IIT Gandhinagar.

<p align="center">
<img width="600" height="400" alt="image" src="https://github.com/user-attachments/assets/629a2e42-8353-4093-922a-cee18552dd53" />
</p>

### Technical Perspective

Mr. Mohamed Kassem, Co-founder and CTO of ChipFoundry

<p align="center">
<img width="600" height="400" alt="image" src="https://github.com/user-attachments/assets/2c177878-9381-48a5-bd36-ff852024e8a8" />
</p>

### Program Structure

<p align="center">
<img width="600" height="400" alt="image" src="https://github.com/user-attachments/assets/b63bb478-c898-4830-a0a4-207f35f52e80" />
</p>

<p align="center">
<img width="600" height="400" alt="image" src="https://github.com/user-attachments/assets/9c8d531c-283d-4d61-b02f-fb9ee001a5e4" />
</p>

### Meet our Team members

<p align="center">
<img width="600" height="400" alt="image" src="https://github.com/user-attachments/assets/b727c9ff-42bc-4c14-a96c-69e4ce82159f" />
</p>

### I am very much thankful to Mr. Kunal Ghosh, VLSI System Design(VSD)

<p align="center">
<img width="300" height="500" alt="image" src="https://github.com/user-attachments/assets/d6ad12ab-693f-48e2-9860-e55bf9fdcb72" />
</p>


<hr style="height:3px; background-color:black; border:none;">



# 🚀Task 2: Tools Installation

Here, I am going to document the list of PC requirements, the tools required, and the steps to install them.

### Steps to install Tools

First, we have to install Oracle Virtual Machine using the link below

https://www.oracle.com/in/virtualization/technologies/vm/downloads/virtualbox-downloads.html

After installing VMware in your Windows system, download the Ubuntu 20.04 or higher version using the link below.

https://ubuntu.com/download

Now, start the Virtual Machine and install the Ubuntu OS check these requirements
- 6 RAM
- 50GB Virtual Disk
- Ubuntu 20.04 or Higher
- 4vCPU

 After the installation of Ubuntu.

 ### Install the open-source EDA tools and verify them using the commands below.

<hr style="height:3px; background-color:black; border:none;">

 ## ⚙️Yosys 
 
```
$ sudo apt-get update
$ git clone https://github.com/YosysHQ/yosys.git
$ cd yosys
$ sudo apt install make               # If make is not installed
$ sudo apt-get install build-essential clang bison flex \
    libreadline-dev gawk tcl-dev libffi-dev git \
    graphviz xdot pkg-config python3 libboost-system-dev \
    libboost-python-dev libboost-filesystem-dev zlib1g-dev
$ make config-gcc
# Yosys build depends on a Git submodule called abc, which hasn't been initialized yet. You need to run the following command before running make
$ git submodule update --init --recursive
$ make 
$ sudo make install
```

<img width="825" height="788" alt="Screenshot 2025-09-21 171958" src="https://github.com/user-attachments/assets/26b4ec4c-e893-4845-b46b-33e166481dd1" />

<hr style="height:3px; background-color:black; border:none;">

## ⚙️iverilog

```
$ sudo apt-get update
$ sudo apt-get install iverilog
```

<img width="826" height="744" alt="Screenshot 2025-09-21 172915" src="https://github.com/user-attachments/assets/f6f86a64-026d-44d3-aa87-b83e06ea0368" />

<hr style="height:3px; background-color:black; border:none;">

## ⚙️gtkwave

```
$ sudo apt-get update
$ sudo apt install gtkwave
```

<img width="835" height="183" alt="Screenshot 2025-09-21 173537" src="https://github.com/user-attachments/assets/824ef2d1-8fd0-4dd0-b366-a1b34ebea02d" />




