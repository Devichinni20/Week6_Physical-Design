# PHYSICAL DESIGN (RTL2GDS FLOW)
<img width="1018" height="458" alt="image" src="https://github.com/user-attachments/assets/4789c44e-9396-4ede-b1f7-a5bac01a0f76" />
<img width="1023" height="93" alt="image" src="https://github.com/user-attachments/assets/a6f20dc6-76a0-4f1d-9f44-733af9bfac48" />

## Day 1 - Inception of open-source EDA, OpenLANE and Sky130 PDK 
<details>
  <summary>
 THEORY
  </summary>

  #### Package

* In any embedded board we have seen, the part of the board we consider as the chip is only the ***PACKAGE*** of the chip which is nothing but a protective layer or packet bound over the actual chip and the actual manufatured chip is usually present at the center of a package wherein, the connections from package is fed to the chip by ***WIRE BOUND*** method which is none other than basic wired connection.
<img width="1920" height="1080" alt="Screenshot (225)" src="https://github.com/user-attachments/assets/813cdc24-e0af-4c6c-a259-3ca1a7b5d903" />



#### Chip

* Now, taking a look inside the chip, all the signals from the external world to the chip and vice versa is passed through ***PADS***. The area bound by the pads is ***CORE*** where all the digital logic of the chip is placed. Both the core and pads make up the ***DIE*** which is the basic manufacturing unit in regards to semiconductor chips.

<img width="1920" height="1080" alt="Screenshot (226)" src="https://github.com/user-attachments/assets/5043c5dd-b998-47de-b729-91b7600d0349" />

<img width="1920" height="1080" alt="Screenshot (227)" src="https://github.com/user-attachments/assets/d1fd3ccb-675e-41d6-b8fc-910ea257cd1d" />

<img width="1920" height="1080" alt="Screenshot (228)" src="https://github.com/user-attachments/assets/b6517494-4483-4642-8a90-8bf6850e8c35" />



* ***FOUNDRY*** is the place where the semiconductor chips are manufactured and ***FOUNDRY IP's*** are Intellectual Properties based on a specific foundry and these IP's require a specific level of intelligence to be produced whereas, repeatable digital logic blocks are called ***MACROS***.


<img width="1920" height="1080" alt="Screenshot (229)" src="https://github.com/user-attachments/assets/23ffc29e-e62a-4dda-a96b-d06047fe2885" />

<img width="1920" height="1080" alt="Screenshot (230)" src="https://github.com/user-attachments/assets/e832ce18-14e5-47ad-8a8a-211c639b75c4" />


#### ISA (Intruction Set Architecture)

* A C program which has to be run on a specific hardware layout which is the interior of a chip in your laptop, there is certain flow to be followed.
* Initially, this particular C program is compiled in it's assembly language program which is nothing but ***RISC-V ISA (Reduced Instruction Set Compting - V Intruction Set Architecture)***.
* Following this, the assembly language program is then converted to machine language program which is the binary language logic 0 and 1 which is understood by the hardware of the computer.
* Directly after this, we've to implement this RISC-V specification using some ***RTL (a Hardware Description Language)***. Finally, from the RTL to ***Layout*** it is a standard PnR or RTL to GDSII flow.


<img width="1920" height="1080" alt="Screenshot (231)" src="https://github.com/user-attachments/assets/1a12eeb1-a99c-4253-82f4-8b2adcdd07ea" />



* For an application software to be run on a hardware there are several processes taking place. To begin with, the apps enters into a block called system software and it converts the application program to binary language. There are various layers in system software in which the major layers or components are OS (Operating System), Compiler and Assembler.
* At first the OS outputs are small function in C, C++, VB or Java language which are taken by the respective compiler and converted into instructions and the syntax of these instructions varies with the hardware architecture on which the system is implemented.
* Then, the job of the assembler is to take these instructions and convert it into it's binary format which is basically called as a machine language program. Finally, this binary language is fed to the hardware and it understands the specific functions it has to perform based on the binary code it receives.
<img width="1920" height="1080" alt="Screenshot (232)" src="https://github.com/user-attachments/assets/df707b86-b84c-449b-aea3-e0f85169adf8" />






* For example, if we take a stopwatch app on RISC-V core, then the output of the OS could be a small C function which enters into the compiler and we get output RISC-V instructions following this, the output of the assembler will be the binary code which enters into your chip layout.


<img width="1920" height="1080" alt="Screenshot (234)" src="https://github.com/user-attachments/assets/d3bc947f-5d05-4070-881c-7cc940f41593" />


 For the above stopwatch the following are the input and output of the compiler and assembler.
<img width="776" height="444" alt="image" src="https://github.com/user-attachments/assets/70967e2b-fc4d-4eef-a30b-810f0fb44ec5" />




* The output of the compiler are instructions and the output of the assembler is the binary pattern. Now, we need some RTL (a Hardware Description Language) which understands and implements the particular instructions. Then, this RTL is synthesised into a netlist in form of gates which is fabricated into the chip through a physical design implementation.

<img width="1920" height="1080" alt="Screenshot (235)" src="https://github.com/user-attachments/assets/c597b1f0-2be9-45b5-92ce-b2b52433d042" />

<img width="1920" height="1080" alt="Screenshot (236)" src="https://github.com/user-attachments/assets/5a26d3ff-b6b5-43ce-a402-0bd9388f0690" />




* There are mainly 3 different parts in this course. They are:
1. RISC-V ISA
2. RTL and synthesis of RISC-V based CPU core - picorv32
3. Physical design implementation of picorv32

<img width="778" height="450" alt="image" src="https://github.com/user-attachments/assets/25dadcf1-ac25-473e-8f85-fd05cc915c93" />



#### Open-source Implementation

* For open-source ASIC design implemantation, we require the following enablers to be readily available as open-source versions. They are:-
1. RTL Designs
2. EDA Tools
3. PDK Data
<img width="1920" height="1080" alt="Screenshot (237)" src="https://github.com/user-attachments/assets/aefff7b6-55c5-49d5-8fd0-3986b7da7e9e" />


* Initially in the early ages, the design and fabrication of IC's were tightly coupled and were only practiced by very few companies like TI, Intel, etc.
* In 1979, Lynn Conway and Carver Mead came up with an idea to saperate the design from the fabrication and to do this they inroduced structured design methodologies based on the λ-based design rules and published the first VLSI book "Introduction to VLSI System" which started the VLSI education.
* This methodology resulted in the emergence of the design only companies or ***"Fabless Companies"*** and fabrication only companies that we usually refer to as ***"Pure Play Fabs"***.
* The inteface between the designers and the fab by now became a set of data files and documents, that are reffered to as the ***"Process Design Kits (PDKs)"***.
* The PDK include but not limited to Device Models, Technology Information, Design Rules, Digital Standard Cell Libraries, I/O Libraries and many more.
* Since, the PDK contained variety of informations, and so they were distributed only under NDAs (Non-Disclosure Agreements) which made it in-accessible to the public.
* Recently, Google worked out an agreement with skywater to open-source the PDK for the 130nm process by skywater Technology, as a result on 30 June 2020 Google released the first ever open-source PDK.

<img width="805" height="429" alt="image" src="https://github.com/user-attachments/assets/2efdc7c3-6b1a-4733-b7d6-a925eb59ae98" />




* ASIC design is a complex step that involves tons of steps, various methodologies and respective EDA tools which are all required for successful ASIC implementation which is achieved though an ASIC flow which is nothing but a piece of software that pulls different tools togather to carry out the design process.

<img width="1920" height="1080" alt="Screenshot (240)" src="https://github.com/user-attachments/assets/48829eb1-4b87-4d89-bd94-4026957e75d9" />

#### OpenLANE Open-source ASIC Design Implementation Flow

* The main objective of the ASIC Design Flow is to take the design from the RTL (Register Transfer Level) all the way to the GDSII, which is the format used for the final fabrication layout.

<img width="1920" height="1080" alt="Screenshot (241)" src="https://github.com/user-attachments/assets/7bf08217-08ea-486e-a462-8a1be5df6d63" />

* Synthesis is the process of convertion or translation of design RTL into circuits made out of Standard Cell Libraries (SCL) the resultant circuit is described in HDL and is usually reffered to as the Gate-Level Netlist.
* Gate-Level Netlist is functionally equivalent to the RTL.
<img width="1732" height="526" alt="Screenshot 2025-10-28 192530" src="https://github.com/user-attachments/assets/d317a8f3-e98e-4e8f-a420-dcc296776160" />


* The fundemental building blocks which are the standard cells have regular layouts.
* Each cell has different views/models which are utilised by different EDA tools like liberty view with electrical models of the cells, HDL behavioral models, SPICE or CDL views of the cells, Layout view which include GDSII view which is the detailed view and LEF view which is the abstract view.
<img width="1192" height="448" alt="Screenshot 2025-10-28 193039" src="https://github.com/user-attachments/assets/60ac3b39-1d0a-42e0-85b0-99f3ce7f4970" />



* Chip Floor Planning

<img width="1920" height="1080" alt="Screenshot (242)" src="https://github.com/user-attachments/assets/6108a29a-2cc5-4a5b-9784-6a29ab9dc675" />

* Macro Floor Planning
<img width="1121" height="439" alt="Screenshot 2025-10-29 000246" src="https://github.com/user-attachments/assets/0b29cd47-7d31-4108-bc2e-b1fe5cd3ae8f" />


* Power Planning typically uses upper metal layers for power distribution since thay are thicker than lower metal layers and so have lower resistance and PP is done to avoid electron migration and IR drops.
<img width="1034" height="461" alt="Screenshot 2025-10-29 000305" src="https://github.com/user-attachments/assets/c3c346d1-35ea-4bcf-aa21-bb386c595e55" />


* Placement
<img width="1920" height="1080" alt="Screenshot (243)" src="https://github.com/user-attachments/assets/e08a4ab0-5289-4984-9ac9-80b282ad50ad" />


* Global placement provide approximate locations for all cells based on connectivity but in this stage the cells may be overlapped on each other and in detailed placement the positions obtained from global placements are minimally altered to make it legal (non-overlapping and in site-rows)
<img width="1095" height="467" alt="Screenshot 2025-10-29 001138" src="https://github.com/user-attachments/assets/b89f48f0-4539-4f3e-9807-e4bcbe228fc7" />



* Clock Tree Synthesis

<img width="1920" height="1080" alt="Screenshot (244)" src="https://github.com/user-attachments/assets/8494515d-b6ad-4773-acbf-6f7fe94e6db3" />


* Clock skew is the time difference in arrival of clock at different components.
* Routing
<img width="1920" height="1080" alt="Screenshot (246)" src="https://github.com/user-attachments/assets/9ae0f046-c05b-4db4-a0d2-3faeb314d5cc" />


* skywater PDK has 6 routing layers in which the lowest layer is called the local interconnect layer which is a Titanium Nitride layer the following 5 layers are all Aluminium layers.

<img width="801" height="661" alt="image" src="https://github.com/user-attachments/assets/dfd14b0a-e5a7-4cae-9fff-4d917ba3d43a" />

* Global and Detailed Routing
<img width="1095" height="467" alt="Screenshot 2025-10-29 001138" src="https://github.com/user-attachments/assets/e36135e6-9359-422d-a5b1-375de0f08cb4" />

<img width="1154" height="442" alt="Screenshot 2025-10-29 002455" src="https://github.com/user-attachments/assets/0936fbc3-26b5-4f20-93e4-16e5087b64d8" />

* Once done with the routing the final layout can be generated which undergoes various Sign-Off checks.
* Design Rules Checking (DRC) which verifies that the final layout honours all design fabrication rules.
* Layout Vs Schematic (LVS) which verifies that the final layout functionality matches the gate-level netlist that we started with.
* Static Timing Analysis (STA) to verify that the design runs at the designated clock frequency.
<img width="1920" height="1080" alt="Screenshot (248)" src="https://github.com/user-attachments/assets/0dd6c6ef-6cd5-448e-985c-d4339dcc86ad" />

* OPENLANE
OpenLane is an open-source digital ASIC design flow that automates the process from RTL to GDSII (chip layout). It integrates several tools like Yosys, OpenROAD, Magic, and KLayout to perform synthesis, floorplanning, placement, routing, and signoff checks.
It’s widely used for academic and research purposes to design and tape-out chips using open-source PDKs such as SkyWater 130nm (Sky130).

<img width="1920" height="1080" alt="Screenshot (249)" src="https://github.com/user-attachments/assets/31e15d15-d5dc-4f2a-b9d6-b1f6a73ddb9e" />


<img width="1920" height="1080" alt="Screenshot (250)" src="https://github.com/user-attachments/assets/a0de2fb4-af8f-4c2d-bad4-baec70ce5a5b" />

<img width="1920" height="1080" alt="Screenshot (251)" src="https://github.com/user-attachments/assets/62d68625-d7b4-41b8-9a61-c48d9a87e1a6" />


<img width="1536" height="864" alt="Screenshot (252)" src="https://github.com/user-attachments/assets/142fb8fd-3a78-433e-b839-0297b3f85c7f" />

 ## OpenLane ASIC Design Flow

The OpenLane flow automates the complete RTL-to-GDSII process for ASIC design using open-source tools. It covers all major design stages — from logic synthesis to final layout generation — ensuring Design Rule Check (DRC) and Layout vs. Schematic (LVS) clean results.

 ## Major Stages in the Flow:

Synthesis – Converts RTL (Verilog) into a gate-level netlist using Yosys.

Floorplanning – Defines chip area, power grid, and placement regions.

Placement – Places standard cells optimally using OpenROAD.

Clock Tree Synthesis (CTS) – Builds a balanced clock distribution network.

Routing – Connects all placed cells following design rules.

Physical Verification – Performs DRC and LVS checks using Magic and Netgen.

GDSII Generation – Produces the final mask layout file for fabrication.

<img width="1920" height="1080" alt="Screenshot (253)" src="https://github.com/user-attachments/assets/2e2a5a00-d3a2-48b7-ba8e-40178ffedc20" />


<img width="1920" height="1080" alt="Screenshot (254)" src="https://github.com/user-attachments/assets/44203437-d539-4c5f-9de3-1b08a916e421" />

<img width="1920" height="1080" alt="Screenshot (255)" src="https://github.com/user-attachments/assets/978529ba-5f1d-4f47-a4ce-d3bf929551d8" />


<img width="1920" height="1080" alt="Screenshot (256)" src="https://github.com/user-attachments/assets/9b32c8c7-cdaa-4a6c-bfc4-f88d6dc45d5d" />

<img width="1920" height="1080" alt="Screenshot (257)" src="https://github.com/user-attachments/assets/473afd04-bfea-4df2-a813-bf380b8e5c1b" />


<img width="1920" height="1080" alt="Screenshot (258)" src="https://github.com/user-attachments/assets/53c1a484-db32-4b4b-a7a7-2c2c472a4e41" />


<img width="1920" height="1080" alt="Screenshot (259)" src="https://github.com/user-attachments/assets/39dd9889-18d1-44ca-b832-c335156c91b7" />
<img width="1920" height="1080" alt="Screenshot (260)" src="https://github.com/user-attachments/assets/7adda883-9019-4047-b1e8-9488a87ba780" />
<img width="1920" height="1080" alt="Screenshot (261)" src="https://github.com/user-attachments/assets/928bf520-85ac-442d-922e-49243daaa8f4" />

<img width="1920" height="1080" alt="Screenshot (262)" src="https://github.com/user-attachments/assets/7d70e54b-68a0-412a-a5b1-44ea746d5ecc" />
<img width="1920" height="1080" alt="Screenshot (263)" src="https://github.com/user-attachments/assets/67f5a23f-6398-4f3b-b42e-b4076ec3f442" />


</details>

### Implementation

Section 1 tasks:- 



























































  
