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

<details>
  <summary>
 IMPLEMENTATION
  </summary>


Day  1 Labs :- 
1. Run 'picorv32a' design synthesis using OpenLANE flow and generate necessary outputs.
2. Calculate the flop ratio.

```math
Flop\ Ratio = \frac{Number\ of\ D\ Flip\ Flops}{Total\ Number\ of\ Cells}
```
```math
Percentage\ of\ DFF's = Flop\ Ratio * 100
```

#### 1. Run 'picorv32a' design synthesis using OpenLANE flow and generate necessary outputs.

Commands to invoke the OpenLANE flow and perform synthesis

```bash
# Change directory to openlane flow directory
cd Desktop/work/tools/openlane_working_dir/openlane

# alias docker='docker run -it -v $(pwd):/openLANE_flow -v $PDK_ROOT:$PDK_ROOT -e PDK_ROOT=$PDK_ROOT -u $(id -u $USER):$(id -g $USER) efabless/openlane:v0.21'
# Since we have aliased the long command to 'docker' we can invoke the OpenLANE flow docker sub-system by just running this command
docker
```
```tcl
# Now that we have entered the OpenLANE flow contained docker sub-system we can invoke the OpenLANE flow in the Interactive mode using the following command
./flow.tcl -interactive

# Now that OpenLANE flow is open we have to input the required packages for proper functionality of the OpenLANE flow
package require openlane 0.9

# Now the OpenLANE flow is ready to run any design and initially we have to prep the design creating some necessary files and directories for running a specific design which in our case is 'picorv32a'
prep -design picorv32a

# Now that the design is prepped and ready, we can run synthesis using following command
run_synthesis

# Exit from OpenLANE flow
exit

# Exit from OpenLANE flow docker sub-system
exit
```


<img width="1920" height="923" alt="VirtualBox_Physical_Design_29_10_2025_02_51_04" src="https://github.com/user-attachments/assets/2f88da67-2f2d-41c4-aa39-61b0265f355b" />
<img width="1920" height="923" alt="VirtualBox_Physical_Design_29_10_2025_02_58_32" src="https://github.com/user-attachments/assets/1e5db22c-43a7-4fdd-b97b-4763a1a4563f" />
<img width="1920" height="923" alt="VirtualBox_Physical_Design_29_10_2025_02_59_22" src="https://github.com/user-attachments/assets/e0832110-a52d-42b8-b778-f2c9687b1c69" />

<img width="1920" height="923" alt="VirtualBox_Physical_Design_29_10_2025_02_53_17" src="https://github.com/user-attachments/assets/439a66e9-80ce-43b4-8583-58a74cd5af0a" />


#### 2. Calculate the flop ratio.

Screenshots of synthesis statistics report file with required values highlighted

<img width="1920" height="923" alt="VirtualBox_Physical_Design_29_10_2025_03_08_09" src="https://github.com/user-attachments/assets/7f82a11e-f76d-4169-9bbd-a7bf26f59df4" />


Calculation of Flop Ratio and DFF % from synthesis statistics report file

```math
Flop\ Ratio = \frac{1613}{14876} = 0.108429685
```
```math
Percentage\ of\ DFF's = 0.108429685 * 100 = 10.84296854\ \%
```

#### 3. Reports

<img width="1920" height="923" alt="VirtualBox_Physical_Design_29_10_2025_03_13_50" src="https://github.com/user-attachments/assets/04be7fbe-3715-4cf6-8384-f826744ae6e5" />

<img width="1920" height="923" alt="VirtualBox_Physical_Design_29_10_2025_03_14_11" src="https://github.com/user-attachments/assets/65574d3f-2eb9-4adb-b974-3e0250b43bbf" />


</details>


## Day 2 - Good floorplan vs bad floorplan and introduction to library cells 

<details>
  <summary>
 THEORY-SS
  </summary>

<img width="1920" height="1080" alt="Screenshot (264)" src="https://github.com/user-attachments/assets/e0478ef9-b2b6-4e81-9602-744cf7c5f39b" />
<img width="1920" height="1080" alt="Screenshot (265)" src="https://github.com/user-attachments/assets/44631b06-ef5d-4e54-b03b-6642fdd66b57" />
<img width="1920" height="1080" alt="Screenshot (266)" src="https://github.com/user-attachments/assets/1a70e625-de23-4860-bf8a-7713e66e7f0b" />
<img width="1920" height="1080" alt="Screenshot (267)" src="https://github.com/user-attachments/assets/d52a0b12-22f5-4690-b266-a783a27e3209" />

<img width="1920" height="1080" alt="Screenshot (268)" src="https://github.com/user-attachments/assets/24f2784c-e62b-4c25-9017-dbf4289bb687" />

<img width="1920" height="1080" alt="Screenshot (269)" src="https://github.com/user-attachments/assets/0d466fee-aab7-41dd-a32b-cfb87503d9c3" />

<img width="1920" height="1080" alt="Screenshot (270)" src="https://github.com/user-attachments/assets/3a0bd81e-8858-418e-ae81-d5eb922ce683" />
<img width="1920" height="1080" alt="Screenshot (271)" src="https://github.com/user-attachments/assets/e7b5c9eb-feaa-46ed-86a2-bbcfe79bc23c" />
<img width="1920" height="1080" alt="Screenshot (272)" src="https://github.com/user-attachments/assets/395f9bb0-abfa-4335-aeeb-03438c7be908" />
<img width="1920" height="1080" alt="Screenshot (273)" src="https://github.com/user-attachments/assets/e3d8d7c6-2aa4-4b48-89ae-092061198350" />
<img width="1920" height="1080" alt="Screenshot (274)" src="https://github.com/user-attachments/assets/9d80bbaa-c9ad-4a46-b99f-a1c3bf7ffe0f" />

<img width="1920" height="1080" alt="Screenshot (275)" src="https://github.com/user-attachments/assets/8c3d519d-e38f-4f71-bed0-2cb3ed0ef00e" />
<img width="1920" height="1080" alt="Screenshot (276)" src="https://github.com/user-attachments/assets/4430cd21-462a-44b3-a219-86a7fd9ebd52" />

<img width="1920" height="1080" alt="Screenshot (277)" src="https://github.com/user-attachments/assets/1bd3984f-3162-46c1-8e38-da17357d3de2" />
<img width="1920" height="1080" alt="Screenshot (278)" src="https://github.com/user-attachments/assets/85a87e97-3515-44a8-ac04-0f9f03e34433" />

<img width="1920" height="1080" alt="Screenshot (279)" src="https://github.com/user-attachments/assets/6fd1890b-0e0e-46a3-b532-cd8b48bd9c88" />

<img width="1920" height="1080" alt="Screenshot (280)" src="https://github.com/user-attachments/assets/e83787cd-08c0-4493-9d15-ceb5eaa2571e" />
<img width="1920" height="1080" alt="Screenshot (281)" src="https://github.com/user-attachments/assets/594c30ea-4ff8-4c84-a1fa-2fb4f5831f65" />
<img width="1920" height="1080" alt="Screenshot (283)" src="https://github.com/user-attachments/assets/124a8320-2af8-4148-9507-59b97f836d80" />

<img width="1920" height="1080" alt="Screenshot (285)" src="https://github.com/user-attachments/assets/f56ad165-915e-4153-aafe-99b534de6649" />


<img width="1920" height="1080" alt="Screenshot (287)" src="https://github.com/user-attachments/assets/22aaf824-35fa-43d4-9b1f-e46fb745a200" />

<img width="1920" height="1080" alt="Screenshot (289)" src="https://github.com/user-attachments/assets/d970c0ff-7db2-485f-b10c-2d602c912614" />
<img width="1920" height="1080" alt="Screenshot (290)" src="https://github.com/user-attachments/assets/435b648a-0341-43c6-a314-19f33d9bc960" />

<img width="1920" height="1080" alt="Screenshot (292)" src="https://github.com/user-attachments/assets/8b352953-3748-4455-b2e6-733f0a4e5760" />


<img width="1920" height="1080" alt="Screenshot (296)" src="https://github.com/user-attachments/assets/62e8805d-7eb8-4424-bdc9-d76f423cdc33" />
<img width="1920" height="1080" alt="Screenshot (297)" src="https://github.com/user-attachments/assets/b1d23179-8406-4cbe-a026-11436e449779" />
<img width="1920" height="1080" alt="Screenshot (298)" src="https://github.com/user-attachments/assets/573fcf68-3cee-484c-8fc2-d1a99157a6d4" />


<img width="1920" height="1080" alt="Screenshot (300)" src="https://github.com/user-attachments/assets/dc69232d-0759-4d52-b8e0-c30185652ea3" />

<img width="1920" height="1080" alt="Screenshot (301)" src="https://github.com/user-attachments/assets/0f7de176-e59f-4182-9581-ba3257ddbfd5" />
<img width="1920" height="1080" alt="Screenshot (302)" src="https://github.com/user-attachments/assets/e5b23699-99ca-447a-b09c-47f7e63c7ea5" />

<img width="1920" height="1080" alt="Screenshot (304)" src="https://github.com/user-attachments/assets/cd2b2ca6-57df-48d1-8534-01dc786bbe7c" />

<img width="1920" height="1080" alt="Screenshot (305)" src="https://github.com/user-attachments/assets/f526c532-62a2-4548-9e44-98ab0de9ea3f" />

<img width="1920" height="1080" alt="Screenshot (307)" src="https://github.com/user-attachments/assets/1b22e900-859f-4050-b493-0d6331d30400" />

<img width="1920" height="1080" alt="Screenshot (308)" src="https://github.com/user-attachments/assets/dc0491af-25c6-4282-8cda-9c4570a81c3a" />

<img width="1920" height="1080" alt="Screenshot (309)" src="https://github.com/user-attachments/assets/d0c9dd40-5561-42f8-a067-af85543a87f9" />


<img width="1920" height="1080" alt="Screenshot (310)" src="https://github.com/user-attachments/assets/69ffdbd2-6e35-4008-a3e4-4bace218bcac" />



<img width="1920" height="1080" alt="Screenshot (311)" src="https://github.com/user-attachments/assets/49e34309-e4fe-4f38-b27c-029c5f100e43" />
<img width="1920" height="1080" alt="Screenshot (312)" src="https://github.com/user-attachments/assets/52d798cd-6187-4127-9e8c-e717f25e31c1" />
<img width="1920" height="1080" alt="Screenshot (313)" src="https://github.com/user-attachments/assets/54b0ae39-e1f2-4ae1-b3a5-89308f07e9ed" />


<img width="1920" height="1080" alt="Screenshot (315)" src="https://github.com/user-attachments/assets/69c470fb-cfcd-49a7-b809-2d9964d89f1e" />
<img width="1920" height="1080" alt="Screenshot (316)" src="https://github.com/user-attachments/assets/fe73e580-41a7-4f25-8944-1a84d2158926" />

<img width="1920" height="1080" alt="Screenshot (317)" src="https://github.com/user-attachments/assets/f49279db-1820-4522-9e52-a1acbbe47f51" />


</details>

<details>
  <summary>
 IMPLEMENTATION 
  </summary>

1. Run 'picorv32a' design floorplan using OpenLANE flow and generate necessary outputs.
2. Calculate the die area in microns from the values in floorplan def.
3. Load generated floorplan def in magic tool and explore the floorplan.
4. Run 'picorv32a' design congestion aware placement using OpenLANE flow and generate necessary outputs.
5. Load generated placement def in magic tool and explore the placement.

```math
Area\ of\ die\ in\ microns = Die\ width\ in\ microns * Die\ height\ in\ microns
```

#### 1. Run 'picorv32a' design floorplan using OpenLANE flow and generate necessary outputs.

Commands to invoke the OpenLANE flow and perform floorplan

```bash
# Change directory to openlane flow directory
cd Desktop/work/tools/openlane_working_dir/openlane

# alias docker='docker run -it -v $(pwd):/openLANE_flow -v $PDK_ROOT:$PDK_ROOT -e PDK_ROOT=$PDK_ROOT -u $(id -u $USER):$(id -g $USER) efabless/openlane:v0.21'
# Since we have aliased the long command to 'docker' we can invoke the OpenLANE flow docker sub-system by just running this command
docker
```
```tcl
# Now that we have entered the OpenLANE flow contained docker sub-system we can invoke the OpenLANE flow in the Interactive mode using the following command
./flow.tcl -interactive

# Now that OpenLANE flow is open we have to input the required packages for proper functionality of the OpenLANE flow
package require openlane 0.9

# Now the OpenLANE flow is ready to run any design and initially we have to prep the design creating some necessary files and directories for running a specific design which in our case is 'picorv32a'
prep -design picorv32a

# Now that the design is prepped and ready, we can run synthesis using following command
run_synthesis

# Now we can run floorplan
run_floorplan
```

Screenshot of floorplan run
<img width="1920" height="923" alt="VirtualBox_Physical_Design_29_10_2025_21_01_34" src="https://github.com/user-attachments/assets/61febe85-00ae-40fa-881e-a54aad9c4b8f" />

<img width="1920" height="923" alt="VirtualBox_Physical_Design_29_10_2025_21_02_26" src="https://github.com/user-attachments/assets/1a2754aa-0a73-46ef-8e4c-2a21d9806ce4" />
<img width="1920" height="923" alt="VirtualBox_Physical_Design_29_10_2025_21_13_17" src="https://github.com/user-attachments/assets/fbceb257-1fe0-44e8-8f45-ec5a920772be" />

#### 2. Calculate the die area in microns from the values in floorplan def.

Screenshot of contents of floorplan def


<img width="1920" height="923" alt="VirtualBox_Physical_Design_29_10_2025_21_15_38" src="https://github.com/user-attachments/assets/fc7d6046-0b42-41cb-bab1-c9fb22aa9770" />

According to floorplan def
```math
1000\ Unit\ Distance = 1\ Micron
```
```math
Die\ width\ in\ unit\ distance = 660685 - 0 = 660685
```
```math
Die\ height\ in\ unit\ distance = 671405 - 0 = 671405
```
```math
Distance\ in\ microns = \frac{Value\ in\ Unit\ Distance}{1000}
```
```math
Die\ width\ in\ microns = \frac{660685}{1000} = 660.685\ Microns
```
```math
Die\ height\ in\ microns = \frac{671405}{1000} = 671.405\ Microns
```
```math
Area\ of\ die\ in\ microns = 660.685 * 671.405 = 443587.212425\ Square\ Microns
```

#### 3. Load generated floorplan def in magic tool and explore the floorplan.

Commands to load floorplan def in magic in another terminal

```bash
# Change directory to path containing generated floorplan def
cd Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/17-03_12-06/results/floorplan/

# Command to load the floorplan def in magic tool
magic -T /home/vsduser/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged.lef def read picorv32a.floorplan.def &
```

Screenshots of floorplan def in magic

<img width="1920" height="923" alt="VirtualBox_Physical_Design_29_10_2025_21_23_11" src="https://github.com/user-attachments/assets/5171fe10-af81-46e7-92da-403d9ce89e9b" />
Equidistant placement of ports

<img width="1920" height="923" alt="VirtualBox_Physical_Design_29_10_2025_23_34_59" src="https://github.com/user-attachments/assets/b6589a6b-610b-47de-86d3-bebce8c12538" />

Port layer as set through config.tcl


<img width="1920" height="923" alt="VirtualBox_Physical_Design_29_10_2025_23_37_18" src="https://github.com/user-attachments/assets/0d063720-6796-4c6d-9c15-40c666fe10b4" />

<img width="1920" height="923" alt="VirtualBox_Physical_Design_29_10_2025_23_43_49" src="https://github.com/user-attachments/assets/6e846536-3294-42c7-af7f-a658eec9af8f" />

Decap Cells and Tap Cells

<img width="1920" height="923" alt="VirtualBox_Physical_Design_29_10_2025_23_45_34" src="https://github.com/user-attachments/assets/66322c7c-ba4b-48b9-9ed9-f704d5f5c51a" />

Diogonally equidistant Tap cells
<img width="1920" height="923" alt="VirtualBox_Physical_Design_29_10_2025_23_45_52" src="https://github.com/user-attachments/assets/5224c7ff-41ba-4e6a-9cfd-a4dbb155e2e2" />

Unplaced standard cells at the origin

<img width="1920" height="923" alt="VirtualBox_Physical_Design_29_10_2025_23_48_01" src="https://github.com/user-attachments/assets/4dee8829-619f-4d02-a956-6329207a403d" />

#### 4. Run 'picorv32a' design congestion aware placement using OpenLANE flow and generate necessary outputs.

Command to run placement

```tcl
# Congestion aware placement by default
run_placement
```

Screenshots of placement run

<img width="1920" height="923" alt="VirtualBox_Physical_Design_30_10_2025_00_40_58" src="https://github.com/user-attachments/assets/7c3382a5-28c5-4228-b5c5-cb133aba6920" />


#### 5. Load generated placement def in magic tool and explore the placement.

Commands to load placement def in magic in another terminal

```bash
# Change directory to path containing generated placement def
cd Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/17-03_12-06/results/placement/

# Command to load the placement def in magic tool
magic -T /home/vsduser/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged.lef def read picorv32a.placement.def &
```

Screenshots of floorplan def in magic




<img width="1920" height="923" alt="VirtualBox_Physical_Design_30_10_2025_00_47_38" src="https://github.com/user-attachments/assets/b1698374-a526-416b-b4ef-29eca58601ec" />

Standard cells legally placed 
<img width="1920" height="923" alt="VirtualBox_Physical_Design_30_10_2025_00_48_00" src="https://github.com/user-attachments/assets/8f822707-79e5-4158-bb49-2d2b90cee8f9" />


<img width="1920" height="923" alt="VirtualBox_Physical_Design_30_10_2025_00_53_13" src="https://github.com/user-attachments/assets/7ca6c5dc-1dbe-4eb9-b02e-ef43351a9adb" />

Commands to exit from current run

```tcl
# Exit from OpenLANE flow
exit

# Exit from OpenLANE flow docker sub-system
exit
```

</details>

## Day3 - Design library cell using Magic Layout and ngspice characterization 

<details>
  <summary>
 THEORY-SS
  </summary>
<img width="1920" height="1080" alt="Screenshot (318)" src="https://github.com/user-attachments/assets/15491376-4659-477c-beb3-7dc060354366" />


<img width="1920" height="1080" alt="Screenshot (319)" src="https://github.com/user-attachments/assets/1438d96e-9366-4e46-b0f6-42be3a14ad9d" />
<img width="1920" height="1080" alt="Screenshot (320)" src="https://github.com/user-attachments/assets/60d6796a-fa13-429e-891a-d86cd3336ac8" />

<img width="1920" height="1080" alt="Screenshot (321)" src="https://github.com/user-attachments/assets/535acf49-4cf2-4db1-aaae-a17588dabdf2" />

<img width="1920" height="1080" alt="Screenshot (322)" src="https://github.com/user-attachments/assets/c9baf1e3-cbe1-4bb8-880f-4bc12ac4c077" />
<img width="1920" height="1080" alt="Screenshot (323)" src="https://github.com/user-attachments/assets/96b4891b-eef7-4e2f-8717-8cc6f18d9d63" />

<img width="1920" height="1080" alt="Screenshot (325)" src="https://github.com/user-attachments/assets/162a2b02-a957-42bb-a242-f52205f8aa34" />

<img width="1920" height="1080" alt="Screenshot (326)" src="https://github.com/user-attachments/assets/bba966e0-c8ea-4443-9605-8d11c71c52db" />

<img width="1920" height="1080" alt="Screenshot (327)" src="https://github.com/user-attachments/assets/25b73c76-9e6d-4978-b8f5-3c0e3db0e3d0" />

<img width="1920" height="1080" alt="Screenshot (328)" src="https://github.com/user-attachments/assets/617fd5a9-b2d9-408f-9dd7-12ebab2b10ff" />

<img width="1920" height="1080" alt="Screenshot (329)" src="https://github.com/user-attachments/assets/e1208c89-d4bc-43e3-a6a4-adc42aec5196" />

<img width="1920" height="1080" alt="Screenshot (330)" src="https://github.com/user-attachments/assets/55f11332-ac98-4623-b646-b192f6f63743" />
<img width="1920" height="1080" alt="Screenshot (332)" src="https://github.com/user-attachments/assets/e1cff6ac-fa48-4cbd-823a-62411c4f93b8" />

<img width="1920" height="1080" alt="Screenshot (333)" src="https://github.com/user-attachments/assets/45bac8b8-a040-444c-9ba6-8a6960f6fb5f" />
<img width="1920" height="1080" alt="Screenshot (334)" src="https://github.com/user-attachments/assets/f360a2b8-99ac-4841-bf0c-107bbac95108" />


<img width="1920" height="1080" alt="Screenshot (335)" src="https://github.com/user-attachments/assets/978bb083-fea1-4751-b1c7-f25bafea5882" />


<img width="1920" height="1080" alt="Screenshot (336)" src="https://github.com/user-attachments/assets/633a32aa-271f-40d0-a71d-dcfddab447bf" />

<img width="1920" height="1080" alt="Screenshot (338)" src="https://github.com/user-attachments/assets/e90837af-91db-4d7a-8bfb-2aa2d5380f84" />


</details>

<details>
  <summary>
 IMPLEMENTATION
  </summary>

1. Clone custom inverter standard cell design from github repository: [Standard cell design and characterization using OpenLANE flow](https://github.com/nickson-jose/vsdstdcelldesign).
2. Load the custom inverter layout in magic and explore.
3. Spice extraction of inverter in magic.
4. Editing the spice model file for analysis through simulation.
5. Post-layout ngspice simulations.
6. Find problem in the DRC section of the old magic tech file for the skywater process and fix them.


#### 1. Clone custom inverter standard cell design from github repository

```bash
# Change directory to openlane
cd Desktop/work/tools/openlane_working_dir/openlane

# Clone the repository with custom inverter design
git clone https://github.com/nickson-jose/vsdstdcelldesign

# Change into repository directory
cd vsdstdcelldesign

# Copy magic tech file to the repo directory for easy access
cp /home/vsduser/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech .

# Check contents whether everything is present
ls

# Command to open custom inverter layout in magic
magic -T sky130A.tech sky130_inv.mag &
```

Screenshot of commands run
<img width="1920" height="923" alt="VirtualBox_Physical_Design_30_10_2025_01_51_10" src="https://github.com/user-attachments/assets/e87ac8af-58d9-4c3e-b720-f4b9f019dfb8" />

#### 2. Load the custom inverter layout in magic and explore.

Screenshot of custom inverter layout in magic
<img width="402" height="378" alt="image" src="https://github.com/user-attachments/assets/684055e3-066e-4a2b-a9b0-a36eba2cf168" />

NMOS and PMOS identified

<img width="1920" height="923" alt="VirtualBox_Physical_Design_30_10_2025_01_53_55" src="https://github.com/user-attachments/assets/17615fd8-e5d4-425b-a4c2-8245c2a969c0" />

Output Y connectivity to PMOS and NMOS drain verified

<img width="1920" height="923" alt="VirtualBox_Physical_Design_30_10_2025_21_03_20" src="https://github.com/user-attachments/assets/ed545a31-34ed-4aa2-a909-f56d273f559f" />

PMOS source connectivity to VDD (here VPWR) verified

<img width="1920" height="923" alt="VirtualBox_Physical_Design_30_10_2025_21_03_46" src="https://github.com/user-attachments/assets/9a247b74-c804-4b53-92ba-6c363888590b" />

Deleting necessary layout part to see DRC error
<img width="773" height="411" alt="image" src="https://github.com/user-attachments/assets/f7c9d7ba-efee-40b3-91f6-fe308a9e3857" />


#### 3. Spice extraction of inverter in magic.

Commands for spice extraction of the custom inverter layout to be used in tkcon window of magic

```tcl
# Check current directory
pwd

# Extraction command to extract to .ext format
extract all

# Before converting ext to spice this command enable the parasitic extraction also
ext2spice cthresh 0 rthresh 0

# Converting to ext to spice
ext2spice
```

Screenshot of tkcon window after running above commands

<img width="1920" height="923" alt="VirtualBox_Physical_Design_30_10_2025_21_20_26" src="https://github.com/user-attachments/assets/91db13c5-2f1d-49da-861d-d0b83585ee1d" />


Screenshot of created spice file

<img width="1920" height="923" alt="VirtualBox_Physical_Design_30_10_2025_21_22_30" src="https://github.com/user-attachments/assets/1f1c2d73-6ef9-4bc8-b786-97933ec1c929" />
#### 4. Editing the spice model file for analysis through simulation.

Measuring unit distance in layout grid
<img width="1920" height="923" alt="VirtualBox_Physical_Design_31_10_2025_01_13_27" src="https://github.com/user-attachments/assets/4af392b1-d352-4e16-97a6-9cb935d49975" />
Final edited spice file ready for ngspice simulation

<img width="1920" height="923" alt="VirtualBox_Physical_Design_31_10_2025_01_31_08" src="https://github.com/user-attachments/assets/a33e1723-f7d3-45a3-b571-cd91e707c8a4" />


#### 5. Post-layout ngspice simulations.

Commands for ngspice simulation

```bash
# Command to directly load spice file for simulation to ngspice
ngspice sky130_inv.spice

# Now that we have entered ngspice with the simulation spice file loaded we just have to load the plot
plot y vs time a
```

Screenshots of ngspice run

<img width="1920" height="923" alt="VirtualBox_Physical_Design_31_10_2025_01_42_32" src="https://github.com/user-attachments/assets/a70edbff-14b8-4839-a591-7fa71492abb6" />
Screenshot of generated plot

<img width="1920" height="923" alt="VirtualBox_Physical_Design_31_10_2025_01_44_12" src="https://github.com/user-attachments/assets/d8483c6e-c117-4ff8-8187-958e92c189b7" />

Rise transition time calculation

```math
Rise\ transition\ time = Time\ taken\ for\ output\ to\ rise\ to\ 80\% - Time\ taken\ for\ output\ to\ rise\ to\ 20\%
```
```math
20\%\ of\ output = 660\ mV
```
```math
80\%\ of\ output = 2.64\ V
```

20% Screenshots

<img width="762" height="437" alt="image" src="https://github.com/user-attachments/assets/ca044b10-4de3-4ac8-be99-68986c67ca07" />
<img width="762" height="427" alt="image" src="https://github.com/user-attachments/assets/831ab7ff-15cc-4f8f-b1ba-1c61ed6d6383" />

80% Screenshots

<img width="712" height="404" alt="image" src="https://github.com/user-attachments/assets/1cc8aee8-97da-47b5-bd75-f1e7c32e2134" />
<img width="739" height="416" alt="image" src="https://github.com/user-attachments/assets/2b3ca48a-137b-4bd5-a466-b2ad2bf500de" />

```math
Rise\ transition\ time = 2.24638 - 2.18242 = 0.06396\ ns = 63.96\ ps
```

Fall transition time calculation

```math
Fall\ transition\ time = Time\ taken\ for\ output\ to\ fall\ to\ 20\% - Time\ taken\ for\ output\ to\ fall\ to\ 80\%
```
```math
20\%\ of\ output = 660\ mV
```
```math
80\%\ of\ output = 2.64\ V
```

20% Screenshots

<img width="757" height="420" alt="image" src="https://github.com/user-attachments/assets/a0a98d68-0276-4de3-b8dd-833607de15ea" />
<img width="723" height="421" alt="image" src="https://github.com/user-attachments/assets/118569bd-6e3d-4e42-adc6-c1e650fa3203" />

80% Screenshots

<img width="743" height="415" alt="image" src="https://github.com/user-attachments/assets/a3c9145e-d8a5-43e7-9295-1e5c80e06a32" />
<img width="656" height="423" alt="image" src="https://github.com/user-attachments/assets/d0b37117-d806-4bff-a42f-d66f04423af7" />


```math
Fall\ transition\ time = 4.0955 - 4.0536 = 0.0419\ ns = 41.9\ ps
```

Rise Cell Delay Calculation

```math
Rise\ Cell\ Delay = Time\ taken\ for\ output\ to\ rise\ to\ 50\% - Time\ taken\ for\ input\ to\ fall\ to\ 50\%
```
```math
50\%\ of\ 3.3\ V = 1.65\ V
```

50% Screenshots

<img width="721" height="406" alt="image" src="https://github.com/user-attachments/assets/f2b01748-6dc1-4685-b8f4-c3b649d43911" />
<img width="739" height="422" alt="image" src="https://github.com/user-attachments/assets/0f68032d-7a23-49c0-94dd-9aa9b4d34203" />



```math
Rise\ Cell\ Delay = 2.21144 - 2.15008 = 0.06136\ ns = 61.36\ ps
```

Fall Cell Delay Calculation


```math
Fall\ Cell\ Delay = Time\ taken\ for\ output\ to\ fall\ to\ 50\% - Time\ taken\ for\ input\ to\ rise\ to\ 50\%
```
```math
50\%\ of\ 3.3\ V = 1.65\ V
```

50% Screenshots

<img width="721" height="410" alt="image" src="https://github.com/user-attachments/assets/7c4d8a9b-6188-4947-809b-b5723aeb0369" />


```math
Fall\ Cell\ Delay = 4.07 - 4.05 = 0.02\ ns = 20\ ps
```



#### 6. Find problem in the DRC section of the old magic tech file for the skywater process and fix them.

Link to Sky130 Periphery rules: [https://skywater-pdk.readthedocs.io/en/main/rules/periphery.html](https://skywater-pdk.readthedocs.io/en/main/rules/periphery.html)

Commands to download and view the corrupted skywater process magic tech file and associated files to perform drc corrections

```bash
# Change to home directory
cd

# Command to download the lab files
wget http://opencircuitdesign.com/open_pdks/archive/drc_tests.tgz

# Since lab file is compressed command to extract it
tar xfz drc_tests.tgz

# Change directory into the lab folder
cd drc_tests

# List all files and directories present in the current directory
ls -al

# Command to view .magicrc file
gvim .magicrc

# Command to open magic tool in better graphics
magic -d XR &
```

Screenshots of commands run

<img width="1920" height="923" alt="VirtualBox_Physical_Design_31_10_2025_19_27_48" src="https://github.com/user-attachments/assets/29a6c994-a0aa-4bb3-b760-2c396ad1639b" />
<img width="1920" height="923" alt="VirtualBox_Physical_Design_31_10_2025_19_30_00" src="https://github.com/user-attachments/assets/b178191b-cdc4-4c93-90c9-6e6c76176d27" />


Screenshot of .magicrc file

<img width="1920" height="923" alt="VirtualBox_Physical_Design_31_10_2025_19_32_38" src="https://github.com/user-attachments/assets/5d505897-efd9-4dc4-a988-3c4a0fa5d713" />

**Incorrectly implemented poly.9 simple rule correction**

Screenshot of poly rules

<img width="854" height="453" alt="image" src="https://github.com/user-attachments/assets/c4cb336d-c029-42b5-adc7-35a2f290ce12" />

Incorrectly implemented poly.9 rule no drc violation even though spacing < 0.48u

<img width="1920" height="923" alt="VirtualBox_Physical_Design_31_10_2025_20_54_37" src="https://github.com/user-attachments/assets/4e226b6d-a716-40d6-a325-eb0536a25a79" />

<img width="1920" height="923" alt="VirtualBox_Physical_Design_31_10_2025_20_54_29" src="https://github.com/user-attachments/assets/e56679a7-c3ec-4dab-ab19-a837c3afc678" />


New commands inserted in sky130A.tech file to update drc

<img width="852" height="473" alt="image" src="https://github.com/user-attachments/assets/acfc12fa-23f0-4258-b475-b30bc4ef0e0e" />
<img width="860" height="455" alt="image" src="https://github.com/user-attachments/assets/72509a8e-9564-4fc2-b43c-ba139528080f" />

Commands to run in tkcon window

```tcl
# Loading updated tech file
tech load sky130A.tech

# Must re-run drc check to see updated drc errors
drc check

# Selecting region displaying the new errors and getting the error messages 
drc why
```

Screenshot of magic window with rule implemented

<img width="998" height="554" alt="image" src="https://github.com/user-attachments/assets/2e4b5601-88ba-4d4b-be57-fb0e44d52d1b" />
<img width="943" height="504" alt="image" src="https://github.com/user-attachments/assets/b39f7863-8a32-4311-884a-c7c5b63c921a" />

**Incorrectly implemented difftap.2 simple rule correction**

Screenshot of difftap rules

<img width="989" height="529" alt="image" src="https://github.com/user-attachments/assets/473bf8d4-c86d-402c-a620-6a51633db302" />

Incorrectly implemented difftap.2 rule no drc violation even though spacing < 0.42u

<img width="992" height="543" alt="image" src="https://github.com/user-attachments/assets/a4bd0507-68e3-4819-9871-32402f9b6b1e" />

New commands inserted in sky130A.tech file to update drc

<img width="993" height="549" alt="image" src="https://github.com/user-attachments/assets/53fe14d6-a91a-44d2-80d1-611b4b15647c" />

Commands to run in tkcon window

```tcl
# Loading updated tech file
tech load sky130A.tech

# Must re-run drc check to see updated drc errors
drc check

# Selecting region displaying the new errors and getting the error messages 
drc why
```

Screenshot of magic window with rule implemented

<img width="999" height="548" alt="image" src="https://github.com/user-attachments/assets/80bf0981-bd01-4ba6-a922-75c4bc6a787b" />

**Incorrectly implemented nwell.4 complex rule correction**

Screenshot of nwell rules

<img width="990" height="525" alt="image" src="https://github.com/user-attachments/assets/5e07ac20-a2fd-4d47-bf8b-ee38197ab64b" />

Incorrectly implemented nwell.4 rule no drc violation even though no tap present in nwell

<img width="995" height="538" alt="image" src="https://github.com/user-attachments/assets/99859af6-918c-4aaf-9199-7c8b56a8f24f" />

New commands inserted in sky130A.tech file to update drc

<img width="993" height="545" alt="image" src="https://github.com/user-attachments/assets/1a7b4f85-a27f-410b-a502-9953625145c8" />
<img width="995" height="543" alt="image" src="https://github.com/user-attachments/assets/967c8b25-3ec2-48b5-ba60-9312e2046ead" />

Commands to run in tkcon window

```tcl
# Loading updated tech file
tech load sky130A.tech

# Change drc style to drc full
drc style drc(full)

# Must re-run drc check to see updated drc errors
drc check

# Selecting region displaying the new errors and getting the error messages 
drc why
```

Screenshot of magic window with rule implemented

<img width="995" height="543" alt="image" src="https://github.com/user-attachments/assets/b5e743fa-1c81-4ad9-991b-46e1e0438e50" />

</details>


## Day 4 - Pre-layout timing analysis and importance of good clock tree 


<details>
  <summary>
 THEORY
  </summary>
  
#### 1. POWER ANALAYSIS
<img width="1920" height="1080" alt="Screenshot (350)" src="https://github.com/user-attachments/assets/c0b90c48-0404-41cb-8bf1-cce43729c40e" />

<img width="1920" height="1080" alt="Screenshot (351)" src="https://github.com/user-attachments/assets/dedde3a1-fcb5-4049-a72e-efaeb38ee66b" />
<img width="1920" height="1080" alt="Screenshot (352)" src="https://github.com/user-attachments/assets/942659a5-ca8d-49fd-b9be-195852bc40ce" />

<img width="1920" height="1080" alt="Screenshot (353)" src="https://github.com/user-attachments/assets/6883024d-4b3f-47e5-8a00-7f670c3f7369" />

<img width="1920" height="1080" alt="Screenshot (354)" src="https://github.com/user-attachments/assets/b881b5e0-aa73-4d2b-88d1-63e7639702a6" />
<img width="1920" height="1080" alt="Screenshot (355)" src="https://github.com/user-attachments/assets/02ecaf0d-2b89-4b5f-9df7-4e2969ef6017" />
<img width="1920" height="1080" alt="Screenshot (356)" src="https://github.com/user-attachments/assets/19c0454e-a81b-4655-83f0-d546112971ca" />

<img width="1920" height="1080" alt="Screenshot (357)" src="https://github.com/user-attachments/assets/c65618b1-0564-4ba2-b36a-e0e5cd0cf69c" />


<img width="1920" height="1080" alt="Screenshot (359)" src="https://github.com/user-attachments/assets/9f7f4d92-55f8-487f-a1ad-06e5053869f2" />

#### 2.TIMING DELAYS


<img width="1920" height="1080" alt="Screenshot (360)" src="https://github.com/user-attachments/assets/ca8dd3ff-0d1e-42c8-9bc0-929657dd8a05" />

<img width="1920" height="1080" alt="Screenshot (361)" src="https://github.com/user-attachments/assets/3f05cdb0-6128-4175-a222-78312436bab7" />

#### 3.CTS

<img width="1920" height="1080" alt="Screenshot (362)" src="https://github.com/user-attachments/assets/72aad87e-6497-4b9a-b7aa-d33e2830d820" />
<img width="1920" height="1080" alt="Screenshot (365)" src="https://github.com/user-attachments/assets/91c523d3-d1da-4ed2-9a51-da3a7560eb22" />
<img width="1920" height="1080" alt="Screenshot (366)" src="https://github.com/user-attachments/assets/b6cef188-c83b-45e8-ad48-cd702f1b656a" />
<img width="1920" height="1080" alt="Screenshot (362)" src="https://github.com/user-attachments/assets/2ad934f3-505e-4eb8-93ed-02e227f1ab81" />
<img width="1920" height="1080" alt="Screenshot (367)" src="https://github.com/user-attachments/assets/e8fcd43a-6b93-46f7-9205-e596ddc3e94f" />
<img width="1920" height="1080" alt="Screenshot (368)" src="https://github.com/user-attachments/assets/435ca3d7-5391-41bb-a199-7f8616c35bb2" />
<img width="1920" height="1080" alt="Screenshot (366)" src="https://github.com/user-attachments/assets/6fe78bac-c6c5-4cbb-91db-cf6fd07f874d" />
<img width="1920" height="1080" alt="Screenshot (365)" src="https://github.com/user-attachments/assets/0455b062-2a4d-4c2e-84f7-a9063bbed8e6" />
<img width="1920" height="1080" alt="Screenshot (370)" src="https://github.com/user-attachments/assets/ae7129ee-870a-4076-8476-e82e165c3996" />
<img width="1920" height="1080" alt="Screenshot (366)" src="https://github.com/user-attachments/assets/c6f1e4a0-ca45-4659-94d5-6039eb5adc40" />
<img width="1920" height="1080" alt="Screenshot (362)" src="https://github.com/user-attachments/assets/5990a73b-fe3d-4afc-a799-afcf66b3b192" />
<img width="1920" height="1080" alt="Screenshot (365)" src="https://github.com/user-attachments/assets/b2f063de-54ca-462c-bf99-df9d61b3fdd0" />
<img width="1920" height="1080" alt="Screenshot (371)" src="https://github.com/user-attachments/assets/6bd0bd9e-1585-4323-bbe8-0ae25483e692" />
<img width="1920" height="1080" alt="Screenshot (372)" src="https://github.com/user-attachments/assets/65f5f54e-296c-4381-b3c5-835f8903c1f8" />
<img width="1920" height="1080" alt="Screenshot (373)" src="https://github.com/user-attachments/assets/1ef9de46-fcfd-4400-a2d9-b50b97eadd09" />
<img width="1920" height="1080" alt="Screenshot (374)" src="https://github.com/user-attachments/assets/5b170b5f-85a4-4396-8297-d6d76166fab6" />
<img width="1920" height="1080" alt="Screenshot (375)" src="https://github.com/user-attachments/assets/2d0841a4-f8cd-4717-ab2a-95ddf6cef489" />
<img width="1920" height="1080" alt="Screenshot (376)" src="https://github.com/user-attachments/assets/b9358443-ce55-4b24-bab4-9e1b20c94885" />

<img width="1920" height="1080" alt="Screenshot (377)" src="https://github.com/user-attachments/assets/3f645e13-df4c-4937-b807-2a75e7c9ec95" />

<img width="1920" height="1080" alt="Screenshot (378)" src="https://github.com/user-attachments/assets/86cd6e52-52a7-4fea-8552-0eeca09d98df" />

<img width="1920" height="1080" alt="Screenshot (379)" src="https://github.com/user-attachments/assets/20318628-984a-4209-acc4-8ff9470fa90e" />
<img width="1920" height="1080" alt="Screenshot (380)" src="https://github.com/user-attachments/assets/d8cc3803-2923-4237-9028-b1a0949d37a1" />

<img width="1920" height="1080" alt="Screenshot (381)" src="https://github.com/user-attachments/assets/c7d81e00-2296-4cf7-b833-2d4bf60f67ae" />

<img width="1920" height="1080" alt="Screenshot (382)" src="https://github.com/user-attachments/assets/33305da7-9c3b-47ec-ab4a-0274972104aa" />



</details>
  
<details>
  <summary>
 IMPLEMENTATION
  </summary>

* Day 4 tasks:-
1. Fix up small DRC errors and verify the design is ready to be inserted into our flow.
2. Save the finalized layout with custom name and open it.
3. Generate lef from the layout.
4. Copy the newly generated lef and associated required lib files to 'picorv32a' design 'src' directory.
5. Edit 'config.tcl' to change lib file and add the new extra lef into the openlane flow.
6. Run openlane flow synthesis with newly inserted custom inverter cell.
7. Remove/reduce the newly introduced violations with the introduction of custom inverter cell by modifying design parameters.
8. Once synthesis has accepted our custom inverter we can now run floorplan and placement and verify the cell is accepted in PnR flow.
9. Do Post-Synthesis timing analysis with OpenSTA tool.
10. Make timing ECO fixes to remove all violations.
11. Replace the old netlist with the new netlist generated after timing ECO fix and implement the floorplan, placement and cts.
12. Post-CTS OpenROAD timing analysis.
13. Explore post-CTS OpenROAD timing analysis by removing 'sky130_fd_sc_hd__clkbuf_1' cell from clock buffer list variable 'CTS_CLK_BUFFER_LIST'.


#### 1. Fix up small DRC errors and verify the design is ready to be inserted into our flow.

Conditions to be verified before moving forward with custom designed cell layout:
* Condition 1: The input and output ports of the standard cell should lie on the intersection of the vertical and horizontal tracks.
* Condition 2: Width of the standard cell should be odd multiples of the horizontal track pitch.
* Condition 3: Height of the standard cell should be even multiples of the vertical track pitch.

Commands to open the custom inverter layout

```bash
# Change directory to vsdstdcelldesign
cd Desktop/work/tools/openlane_working_dir/openlane/vsdstdcelldesign

# Command to open custom inverter layout in magic
magic -T sky130A.tech sky130_inv.mag &
```

Screenshot of tracks.info of sky130_fd_sc_hd

<img width="1920" height="1080" alt="Screenshot (342)" src="https://github.com/user-attachments/assets/b3d0a89f-2b4c-4325-8d9e-f6cd3d69e033" />

ommands for tkcon window to set grid as tracks of locali layer

```tcl
# Get syntax for grid command
help grid

# Set grid values accordingly
grid 0.46um 0.34um 0.23um 0.17um
```

Screenshot of commands run

<img width="1920" height="1080" alt="Screenshot (343)" src="https://github.com/user-attachments/assets/434f0700-4bde-4615-9910-ffc2467673fc" />
<img width="1920" height="1080" alt="Screenshot (344)" src="https://github.com/user-attachments/assets/332a78fd-dc56-4fdc-be98-9db73410cdec" />

Condition 1 verified

<img width="1920" height="1080" alt="Screenshot (345)" src="https://github.com/user-attachments/assets/7e558a2a-0044-4525-af6f-aaa2ca4ea4e7" />

Condition 2 verified

```math
Horizontal\ track\ pitch = 0.46\ um
```
<img width="772" height="417" alt="image" src="https://github.com/user-attachments/assets/89b1c680-d1b0-4ddf-b52b-9b52328b6f74" />

```math
Width\ of\ standard\ cell = 1.38\ um = 0.46 * 3
```

Condition 3 verified

```math
Vertical\ track\ pitch = 0.34\ um
```

<img width="778" height="418" alt="image" src="https://github.com/user-attachments/assets/8450193d-ea3e-4487-b295-4e9d6952e913" />

```math
Height\ of\ standard\ cell = 2.72\ um = 0.34 * 8
```

#### 2. Save the finalized layout with custom name and open it.

Command for tkcon window to save the layout with custom name

```tcl
# Command to save as
save sky130_vsdinv.mag
```

Command to open the newly saved layout
```bash
# Command to open custom inverter layout in magic
magic -T sky130A.tech sky130_vsdinv.mag &
```

Screenshot of newly saved layout

<img width="1920" height="1080" alt="Screenshot (347)" src="https://github.com/user-attachments/assets/86043802-f695-42ce-9fe4-5671705a63e5" />
<img width="1920" height="1080" alt="Screenshot (348)" src="https://github.com/user-attachments/assets/86e5238d-5b5c-4b7a-87f0-947b166abdf2" />


#### 3. Generate lef from the layout.

Command for tkcon window to write lef

```tcl
# lef command
lef write
```

Screenshot of command run

<img width="773" height="412" alt="image" src="https://github.com/user-attachments/assets/ecb5edf4-8240-4ecb-b46d-d3ff4062ef8b" />

Screenshot of newly created lef file

<img width="1920" height="1080" alt="Screenshot (349)" src="https://github.com/user-attachments/assets/d02a6872-75a1-4d85-80b8-5e12103e04dc" />
<img width="768" height="428" alt="image" src="https://github.com/user-attachments/assets/3caf2e9a-3b81-45d5-a888-5c8e4ac9579b" />

#### 4. Copy the newly generated lef and associated required lib files to 'picorv32a' design 'src' directory.

Commands to copy necessary files to 'picorv32a' design 'src' directory

```bash
# Copy lef file
cp sky130_vsdinv.lef ~/Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/src/

# List and check whether it's copied
ls ~/Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/src/

# Copy lib files
cp libs/sky130_fd_sc_hd__* ~/Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/src/

# List and check whether it's copied
ls ~/Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/src/
```

Screenshot of commands run

<img width="780" height="425" alt="image" src="https://github.com/user-attachments/assets/71986b43-f73f-474b-80f6-988a2ea3cc6e" />


#### 5. Edit 'config.tcl' to change lib file and add the new extra lef into the openlane flow.

Commands to be added to config.tcl to include our custom cell in the openlane flow

```tcl
set ::env(LIB_SYNTH) "$::env(OPENLANE_ROOT)/designs/picorv32a/src/sky130_fd_sc_hd__typical.lib"
set ::env(LIB_FASTEST) "$::env(OPENLANE_ROOT)/designs/picorv32a/src/sky130_fd_sc_hd__fast.lib"
set ::env(LIB_SLOWEST) "$::env(OPENLANE_ROOT)/designs/picorv32a/src/sky130_fd_sc_hd__slow.lib"
set ::env(LIB_TYPICAL) "$::env(OPENLANE_ROOT)/designs/picorv32a/src/sky130_fd_sc_hd__typical.lib"

set ::env(EXTRA_LEFS) [glob $::env(OPENLANE_ROOT)/designs/$::env(DESIGN_NAME)/src/*.lef]
```

Edited config.tcl to include the added lef and change library to ones we added in src directory

<img width="769" height="427" alt="image" src="https://github.com/user-attachments/assets/76910c70-25e7-4189-95c5-42bcc5d503bf" />

#### 6. Run openlane flow synthesis with newly inserted custom inverter cell.

Commands to invoke the OpenLANE flow include new lef and perform synthesis 

```bash
# Change directory to openlane flow directory
cd Desktop/work/tools/openlane_working_dir/openlane

# alias docker='docker run -it -v $(pwd):/openLANE_flow -v $PDK_ROOT:$PDK_ROOT -e PDK_ROOT=$PDK_ROOT -u $(id -u $USER):$(id -g $USER) efabless/openlane:v0.21'
# Since we have aliased the long command to 'docker' we can invoke the OpenLANE flow docker sub-system by just running this command
docker
```
```tcl
# Now that we have entered the OpenLANE flow contained docker sub-system we can invoke the OpenLANE flow in the Interactive mode using the following command
./flow.tcl -interactive

# Now that OpenLANE flow is open we have to input the required packages for proper functionality of the OpenLANE flow
package require openlane 0.9

# Now the OpenLANE flow is ready to run any design and initially we have to prep the design creating some necessary files and directories for running a specific design which in our case is 'picorv32a'
prep -design picorv32a

# Adiitional commands to include newly added lef to openlane flow
set lefs [glob $::env(DESIGN_DIR)/src/*.lef]
add_lefs -src $lefs

# Now that the design is prepped and ready, we can run synthesis using following command
run_synthesis
```

Screenshots of commands run

<img width="991" height="542" alt="image" src="https://github.com/user-attachments/assets/f361ff4d-267d-4b32-88e4-685cf19556b5" />
<img width="980" height="523" alt="image" src="https://github.com/user-attachments/assets/0c8d5a14-f49d-4904-8194-afccd9896875" />
<img width="994" height="542" alt="image" src="https://github.com/user-attachments/assets/5b889c13-803c-4f51-ac01-c2461ce97bba" />
<img width="992" height="532" alt="image" src="https://github.com/user-attachments/assets/c60ca229-eca8-45d0-a06b-8aa522b35a85" />

#### 7. Remove/reduce the newly introduced violations with the introduction of custom inverter cell by modifying design parameters.

Noting down current design values generated before modifying parameters to improve timing\

<img width="998" height="540" alt="image" src="https://github.com/user-attachments/assets/3c199875-304a-4b97-83ab-dee55af361b1" />
<img width="991" height="535" alt="image" src="https://github.com/user-attachments/assets/5adf5f4a-341f-416c-b2f0-4b177c4799ab" />

Commands to view and change parameters to improve timing and run synthesis

```tcl
# Now once again we have to prep design so as to update variables
prep -design picorv32a -tag 24-03_10-03 -overwrite

# Addiitional commands to include newly added lef to openlane flow merged.lef
set lefs [glob $::env(DESIGN_DIR)/src/*.lef]
add_lefs -src $lefs

# Command to display current value of variable SYNTH_STRATEGY
echo $::env(SYNTH_STRATEGY)

# Command to set new value for SYNTH_STRATEGY
set ::env(SYNTH_STRATEGY) "DELAY 3"

# Command to display current value of variable SYNTH_BUFFERING to check whether it's enabled
echo $::env(SYNTH_BUFFERING)

# Command to display current value of variable SYNTH_SIZING
echo $::env(SYNTH_SIZING)

# Command to set new value for SYNTH_SIZING
set ::env(SYNTH_SIZING) 1

# Command to display current value of variable SYNTH_DRIVING_CELL to check whether it's the proper cell or not
echo $::env(SYNTH_DRIVING_CELL)

# Now that the design is prepped and ready, we can run synthesis using following command
run_synthesis
```

Screenshot of merged.lef in `tmp` directory with our custom inverter as macro

<img width="996" height="544" alt="image" src="https://github.com/user-attachments/assets/1bba691e-c2fd-48e9-a9c7-44377baa0a08" />

Screenshots of commands run

<img width="1002" height="544" alt="image" src="https://github.com/user-attachments/assets/015171ad-5ff7-4cdd-b49f-a81c196c7f36" />
<img width="983" height="532" alt="image" src="https://github.com/user-attachments/assets/d689a639-c09e-4fcc-ac96-b581e1e55d04" />
<img width="1003" height="522" alt="image" src="https://github.com/user-attachments/assets/0a61ad85-be8c-499b-86ce-5bbdc8fd7058" />

Comparing to previously noted run values area has increased and worst negative slack has become 0

<img width="996" height="540" alt="image" src="https://github.com/user-attachments/assets/9c9985e5-0847-44c3-b234-d20b499cd576" />
<img width="993" height="535" alt="image" src="https://github.com/user-attachments/assets/ba07a2f4-0113-4996-8b37-5882fd82cdb5" />


#### 8. Once synthesis has accepted our custom inverter we can now run floorplan and placement and verify the cell is accepted in PnR flow.

Now that our custom inverter is properly accepted in synthesis we can now run floorplan using following command

```tcl
# Now we can run floorplan
run_floorplan
```

Screenshots of command run

<img width="997" height="543" alt="image" src="https://github.com/user-attachments/assets/1fe492dc-d53a-43e0-be55-1daba4d3849c" />
<img width="994" height="527" alt="image" src="https://github.com/user-attachments/assets/72940558-5f6a-4808-8445-fa9ff13847be" />


Since we are facing unexpected un-explainable error while using `run_floorplan` command, we can instead use the following set of commands available based on information from `Desktop/work/tools/openlane_working_dir/openlane/scripts/tcl_commands/floorplan.tcl` and also based on `Floorplan Commands` section in `Desktop/work/tools/openlane_working_dir/openlane/docs/source/OpenLANE_commands.md`

```tcl
# Follwing commands are alltogather sourced in "run_floorplan" command
init_floorplan
place_io
tap_decap_or
```

Screenshots of commands run

<img width="1004" height="555" alt="image" src="https://github.com/user-attachments/assets/f69be142-91a1-4081-a551-5f575a167f57" />
<img width="1000" height="548" alt="image" src="https://github.com/user-attachments/assets/9b308861-b4c4-44bb-a82a-ba9e0cb7cca9" />
<img width="1009" height="539" alt="image" src="https://github.com/user-attachments/assets/b413bbe2-79d9-415d-86b4-fb2238eba024" />

Now that floorplan is done we can do placement using following command

```tcl
# Now we are ready to run placement
run_placement
```

Screenshots of command run

<img width="993" height="540" alt="image" src="https://github.com/user-attachments/assets/13ccab48-126a-4ef6-9f5d-220f0f290aa2" />
<img width="1000" height="543" alt="image" src="https://github.com/user-attachments/assets/9ac0d1ab-9fbb-4a4e-b667-60f646866361" />

Commands to load placement def in magic in another terminal

```bash
# Change directory to path containing generated placement def
cd Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/24-03_10-03/results/placement/

# Command to load the placement def in magic tool
magic -T /home/vsduser/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged.lef def read picorv32a.placement.def &
```

Screenshot of placement def in magic

<img width="999" height="550" alt="image" src="https://github.com/user-attachments/assets/a8c42bcf-4e05-45ae-a1eb-1d42e01b3a0b" />

Screenshot of custom inverter inserted in placement def with proper abutment

<img width="997" height="542" alt="image" src="https://github.com/user-attachments/assets/61a24699-b840-437d-ae17-050a0b345f16" />


Command for tkcon window to view internal layers of cells

```tcl
# Command to view internal connectivity layers
expand
```

Abutment of power pins with other cell from library clearly visible

<img width="999" height="548" alt="image" src="https://github.com/user-attachments/assets/80e06072-df71-4011-8377-85d2f321aa64" />
<img width="998" height="539" alt="image" src="https://github.com/user-attachments/assets/64b71026-70b2-4a9b-b5df-5611174c1f23" />



#### 9. Do Post-Synthesis timing analysis with OpenSTA tool.

Since we are having 0 wns after improved timing run we are going to do timing analysis on initial run of synthesis which has lots of violations and no parameters were added to improve timing

Commands to invoke the OpenLANE flow include new lef and perform synthesis 

```bash
# Change directory to openlane flow directory
cd Desktop/work/tools/openlane_working_dir/openlane

# alias docker='docker run -it -v $(pwd):/openLANE_flow -v $PDK_ROOT:$PDK_ROOT -e PDK_ROOT=$PDK_ROOT -u $(id -u $USER):$(id -g $USER) efabless/openlane:v0.21'
# Since we have aliased the long command to 'docker' we can invoke the OpenLANE flow docker sub-system by just running this command
docker
```
```tcl
# Now that we have entered the OpenLANE flow contained docker sub-system we can invoke the OpenLANE flow in the Interactive mode using the following command
./flow.tcl -interactive

# Now that OpenLANE flow is open we have to input the required packages for proper functionality of the OpenLANE flow
package require openlane 0.9

# Now the OpenLANE flow is ready to run any design and initially we have to prep the design creating some necessary files and directories for running a specific design which in our case is 'picorv32a'
prep -design picorv32a

# Adiitional commands to include newly added lef to openlane flow
set lefs [glob $::env(DESIGN_DIR)/src/*.lef]
add_lefs -src $lefs

# Command to set new value for SYNTH_SIZING
set ::env(SYNTH_SIZING) 1

# Now that the design is prepped and ready, we can run synthesis using following command
run_synthesis
```

Commands run final screenshot

<img width="999" height="543" alt="image" src="https://github.com/user-attachments/assets/39421e17-9012-4497-96e5-5de550b89e23" />

Newly created `pre_sta.conf` for STA analysis in `openlane` directory

<img width="999" height="547" alt="image" src="https://github.com/user-attachments/assets/9bff5c4e-45db-443e-84de-50b91bca9367" />


Newly created `my_base.sdc` for STA analysis in `openlane/designs/picorv32a/src` directory based on the file `openlane/scripts/base.sdc`

<img width="991" height="548" alt="image" src="https://github.com/user-attachments/assets/eaafc276-bed8-42c3-8e85-85c7b132774f" />

<img width="998" height="532" alt="image" src="https://github.com/user-attachments/assets/eb6089a4-5280-400d-9d25-299a79aa99ef" />


Commands to run STA in another terminal

```bash
# Change directory to openlane
cd Desktop/work/tools/openlane_working_dir/openlane

# Command to invoke OpenSTA tool with script
sta pre_sta.conf
```

Screenshots of commands run

<img width="989" height="555" alt="image" src="https://github.com/user-attachments/assets/bb3a5203-7cb7-4f50-8ecd-94c391845ee3" />

<img width="993" height="530" alt="image" src="https://github.com/user-attachments/assets/2e7a1c4b-29d0-4ce2-a411-43699b9a6da7" />
<img width="996" height="539" alt="image" src="https://github.com/user-attachments/assets/b3a32614-f0b4-4b4e-8a6d-428482b62c29" />
<img width="993" height="526" alt="image" src="https://github.com/user-attachments/assets/00cf6712-b854-47d7-aeae-7c409a004aa7" />

Since more fanout is causing more delay we can add parameter to reduce fanout and do synthesis again

Commands to include new lef and perform synthesis 

```tcl
# Now the OpenLANE flow is ready to run any design and initially we have to prep the design creating some necessary files and directories for running a specific design which in our case is 'picorv32a'
prep -design picorv32a -tag 25-03_18-52 -overwrite

# Adiitional commands to include newly added lef to openlane flow
set lefs [glob $::env(DESIGN_DIR)/src/*.lef]
add_lefs -src $lefs

# Command to set new value for SYNTH_SIZING
set ::env(SYNTH_SIZING) 1

# Command to set new value for SYNTH_MAX_FANOUT
set ::env(SYNTH_MAX_FANOUT) 4

# Command to display current value of variable SYNTH_DRIVING_CELL to check whether it's the proper cell or not
echo $::env(SYNTH_DRIVING_CELL)

# Now that the design is prepped and ready, we can run synthesis using following command
run_synthesis
```

Commands run final screenshot

<img width="1000" height="541" alt="image" src="https://github.com/user-attachments/assets/a78a2988-c106-4f5d-ad45-50cda338512a" />

Commands to run STA in another terminal

```bash
# Change directory to openlane
cd Desktop/work/tools/openlane_working_dir/openlane

# Command to invoke OpenSTA tool with script
sta pre_sta.conf
```

Screenshots of commands run

<img width="993" height="552" alt="image" src="https://github.com/user-attachments/assets/7d08aebe-0e0c-4b95-82f8-4ebfff863c18" />
<img width="985" height="530" alt="image" src="https://github.com/user-attachments/assets/720291bb-bdae-4276-959c-5cb0eadbfd09" />
<img width="973" height="541" alt="image" src="https://github.com/user-attachments/assets/673e1f34-52b4-4eea-b0a4-3512c9cb5c6d" />
<img width="982" height="534" alt="image" src="https://github.com/user-attachments/assets/46750cfd-5b7d-498b-8e49-b66bd6866988" />


#### 10. Make timing ECO fixes to remove all violations.

OR gate of drive strength 2 is driving 4 fanouts

<img width="973" height="539" alt="image" src="https://github.com/user-attachments/assets/ad43770c-3474-4d5f-bb32-028abd2c1654" />


Commands to perform analysis and optimize timing by replacing with OR gate of drive strength 4

```tcl
# Reports all the connections to a net
report_net -connections _11672_

# Checking command syntax
help replace_cell

# Replacing cell
replace_cell _14510_ sky130_fd_sc_hd__or3_4

# Generating custom timing report
report_checks -fields {net cap slew input_pins} -digits 4
```

Result - slack reduced

<img width="987" height="535" alt="image" src="https://github.com/user-attachments/assets/20a2fade-72b7-48b5-90e9-938deabb34a8" />
<img width="980" height="545" alt="image" src="https://github.com/user-attachments/assets/ee3f75a9-4400-4f10-be1d-9968958e8d7c" />
<img width="996" height="540" alt="image" src="https://github.com/user-attachments/assets/357c4721-14af-46e7-8a91-5b1222e78e55" />
<img width="982" height="530" alt="image" src="https://github.com/user-attachments/assets/e128c1b8-1cb9-43a3-b434-afe65a9c8457" />

OR gate of drive strength 2 is driving 4 fanouts

Commands to perform analysis and optimize timing by replacing with OR gate of drive strength 4

```tcl
# Reports all the connections to a net
report_net -connections _11675_

# Replacing cell
replace_cell _14514_ sky130_fd_sc_hd__or3_4

# Generating custom timing report
report_checks -fields {net cap slew input_pins} -digits 4
```

Result - slack reduced

<img width="988" height="543" alt="image" src="https://github.com/user-attachments/assets/25d65bde-a9be-497d-9c20-8be255be8b25" />
<img width="987" height="542" alt="image" src="https://github.com/user-attachments/assets/706c9d92-2041-4ef2-9912-364709572537" />
<img width="983" height="548" alt="image" src="https://github.com/user-attachments/assets/1e182d6e-1881-4159-890e-4c7beeb1e744" />


OR gate of drive strength 2 driving OA gate has more delay

<img width="986" height="549" alt="image" src="https://github.com/user-attachments/assets/7a962abc-f782-48b4-bf19-43983663a5c8" />


Commands to perform analysis and optimize timing by replacing with OR gate of drive strength 4

```tcl
# Reports all the connections to a net
report_net -connections _11643_

# Replacing cell
replace_cell _14481_ sky130_fd_sc_hd__or4_4

# Generating custom timing report
report_checks -fields {net cap slew input_pins} -digits 4
```

Result - slack reduced

<img width="982" height="550" alt="image" src="https://github.com/user-attachments/assets/5537c42c-de51-4fd7-aa00-6cefa6624aee" />
<img width="983" height="532" alt="image" src="https://github.com/user-attachments/assets/2124f949-13df-419a-bea1-f3892247a1e7" />

OR gate of drive strength 2 driving OA gate has more delay

<img width="993" height="547" alt="image" src="https://github.com/user-attachments/assets/cabec99b-c831-4c4d-ac6e-a2e21d2fdd5b" />

Commands to perform analysis and optimize timing by replacing with OR gate of drive strength 4

```tcl
# Reports all the connections to a net
report_net -connections _11668_

# Replacing cell
replace_cell _14506_ sky130_fd_sc_hd__or4_4

# Generating custom timing report
report_checks -fields {net cap slew input_pins} -digits 4
```

Result - slack reduced

<img width="978" height="532" alt="image" src="https://github.com/user-attachments/assets/ac37a68a-4bca-4ab3-87fd-bfc3d2c3ad58" />

<img width="985" height="538" alt="image" src="https://github.com/user-attachments/assets/6e98093a-1ad5-426a-af12-13884863dd16" />

Commands to verify instance `_14506_`  is replaced with `sky130_fd_sc_hd__or4_4`

```tcl
# Generating custom timing report
report_checks -from _29043_ -to _30440_ -through _14506_
```

Screenshot of replaced instance

<img width="988" height="544" alt="image" src="https://github.com/user-attachments/assets/e667cdd6-e047-49c4-b310-90d1b7652eaa" />

*We started ECO fixes at wns -23.9000 and now we stand at wns -22.6173 we reduced around 1.2827 ns of violation*

#### 11. Replace the old netlist with the new netlist generated after timing ECO fix and implement the floorplan, placement and cts.

Now to insert this updated netlist to PnR flow and we can use `write_verilog` and overwrite the synthesis netlist but before that we are going to make a copy of the old old netlist

Commands to make copy of netlist

```bash
# Change from home directory to synthesis results directory
cd Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/25-03_18-52/results/synthesis/

# List contents of the directory
ls

# Copy and rename the netlist
cp picorv32a.synthesis.v picorv32a.synthesis_old.v

# List contents of the directory
ls
```

Screenshot of commands run

<img width="1001" height="530" alt="image" src="https://github.com/user-attachments/assets/ceeb0a39-4f78-4f41-aa27-512bf86ad6e1" />


Commands to write verilog

```tcl
# Check syntax
help write_verilog

# Overwriting current synthesis netlist
write_verilog /home/vsduser/Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/25-03_18-52/results/synthesis/picorv32a.synthesis.v

# Exit from OpenSTA since timing analysis is done
exit
```

Screenshot of commands run

<img width="1005" height="550" alt="image" src="https://github.com/user-attachments/assets/025b060e-b5c2-4951-8fe0-5865ea6049c9" />


Verified that the netlist is overwritten by checking that instance `_14506_`  is replaced with `sky130_fd_sc_hd__or4_4`

<img width="990" height="548" alt="image" src="https://github.com/user-attachments/assets/0a9073d9-8e4c-4abf-b100-7f70754b2c2a" />


Since we confirmed that netlist is replaced and will be loaded in PnR but since we want to follow up on the earlier 0 violation design we are continuing with the clean design to further stages

Commands load the design and run necessary stages

```tcl
# Now once again we have to prep design so as to update variables
prep -design picorv32a -tag 24-03_10-03 -overwrite

# Addiitional commands to include newly added lef to openlane flow merged.lef
set lefs [glob $::env(DESIGN_DIR)/src/*.lef]
add_lefs -src $lefs

# Command to set new value for SYNTH_STRATEGY
set ::env(SYNTH_STRATEGY) "DELAY 3"

# Command to set new value for SYNTH_SIZING
set ::env(SYNTH_SIZING) 1

# Now that the design is prepped and ready, we can run synthesis using following command
run_synthesis

# Follwing commands are alltogather sourced in "run_floorplan" command
init_floorplan
place_io
tap_decap_or

# Now we are ready to run placement
run_placement

# Incase getting error
unset ::env(LIB_CTS)

# With placement done we are now ready to run CTS
run_cts
```

Screenshots of commands run

<img width="1006" height="546" alt="image" src="https://github.com/user-attachments/assets/2420bb19-ea20-495f-a790-4a8f0196c549" />
<img width="985" height="553" alt="image" src="https://github.com/user-attachments/assets/3182df67-cd7a-4257-99d7-8811dc093525" />
<img width="998" height="548" alt="image" src="https://github.com/user-attachments/assets/c0430375-78f7-4a61-bd8a-e228ccb1b32b" />
<img width="996" height="544" alt="image" src="https://github.com/user-attachments/assets/8daa1f7b-27eb-4c50-82d9-f8976dde82bd" />
<img width="1000" height="545" alt="image" src="https://github.com/user-attachments/assets/e5269da8-2a04-41ea-a80a-52ef2c3fdde9" />
<img width="1004" height="553" alt="image" src="https://github.com/user-attachments/assets/cbf6a6bf-6333-4bf0-8318-3139bf102868" />
<img width="998" height="549" alt="image" src="https://github.com/user-attachments/assets/d8049100-1aac-4682-ad91-94d94bcfb3de" />
<img width="1002" height="544" alt="image" src="https://github.com/user-attachments/assets/36a51e3f-636a-4fb2-899a-02ffd238aafa" />


#### 12. Post-CTS OpenROAD timing analysis.

Commands to be run in OpenLANE flow to do OpenROAD timing analysis with integrated OpenSTA in OpenROAD

```tcl
# Command to run OpenROAD tool
openroad

# Reading lef file
read_lef /openLANE_flow/designs/picorv32a/runs/24-03_10-03/tmp/merged.lef

# Reading def file
read_def /openLANE_flow/designs/picorv32a/runs/24-03_10-03/results/cts/picorv32a.cts.def

# Creating an OpenROAD database to work with
write_db pico_cts.db

# Loading the created database in OpenROAD
read_db pico_cts.db

# Read netlist post CTS
read_verilog /openLANE_flow/designs/picorv32a/runs/24-03_10-03/results/synthesis/picorv32a.synthesis_cts.v

# Read library for design
read_liberty $::env(LIB_SYNTH_COMPLETE)

# Link design and library
link_design picorv32a

# Read in the custom sdc we created
read_sdc /openLANE_flow/designs/picorv32a/src/my_base.sdc

# Setting all cloks as propagated clocks
set_propagated_clock [all_clocks]

# Check syntax of 'report_checks' command
help report_checks

# Generating custom timing report
report_checks -path_delay min_max -fields {slew trans net cap input_pins} -format full_clock_expanded -digits 4

# Exit to OpenLANE flow
exit
```

Screenshots of commands run and timing report generated

<img width="992" height="554" alt="image" src="https://github.com/user-attachments/assets/eaecaf56-eb9f-476a-9548-f2ea034e82bd" />
<img width="1000" height="549" alt="image" src="https://github.com/user-attachments/assets/b94dfd5f-72fc-4c4a-9755-9bf5762e98f5" />
<img width="981" height="548" alt="image" src="https://github.com/user-attachments/assets/a9c46908-9100-4d2d-9005-d1a0452bee74" />
<img width="984" height="546" alt="image" src="https://github.com/user-attachments/assets/42c47bce-23f4-4dc5-b243-974e50f999ca" />

#### 13. Explore post-CTS OpenROAD timing analysis by removing 'sky130_fd_sc_hd__clkbuf_1' cell from clock buffer list variable 'CTS_CLK_BUFFER_LIST'.

Commands to be run in OpenLANE flow to do OpenROAD timing analysis after changing `CTS_CLK_BUFFER_LIST`

```tcl
# Checking current value of 'CTS_CLK_BUFFER_LIST'
echo $::env(CTS_CLK_BUFFER_LIST)

# Removing 'sky130_fd_sc_hd__clkbuf_1' from the list
set ::env(CTS_CLK_BUFFER_LIST) [lreplace $::env(CTS_CLK_BUFFER_LIST) 0 0]

# Checking current value of 'CTS_CLK_BUFFER_LIST'
echo $::env(CTS_CLK_BUFFER_LIST)

# Checking current value of 'CURRENT_DEF'
echo $::env(CURRENT_DEF)

# Setting def as placement def
set ::env(CURRENT_DEF) /openLANE_flow/designs/picorv32a/runs/24-03_10-03/results/placement/picorv32a.placement.def

# Run CTS again
run_cts

# Checking current value of 'CTS_CLK_BUFFER_LIST'
echo $::env(CTS_CLK_BUFFER_LIST)

# Command to run OpenROAD tool
openroad

# Reading lef file
read_lef /openLANE_flow/designs/picorv32a/runs/24-03_10-03/tmp/merged.lef

# Reading def file
read_def /openLANE_flow/designs/picorv32a/runs/24-03_10-03/results/cts/picorv32a.cts.def

# Creating an OpenROAD database to work with
write_db pico_cts1.db

# Loading the created database in OpenROAD
read_db pico_cts.db

# Read netlist post CTS
read_verilog /openLANE_flow/designs/picorv32a/runs/24-03_10-03/results/synthesis/picorv32a.synthesis_cts.v

# Read library for design
read_liberty $::env(LIB_SYNTH_COMPLETE)

# Link design and library
link_design picorv32a

# Read in the custom sdc we created
read_sdc /openLANE_flow/designs/picorv32a/src/my_base.sdc

# Setting all cloks as propagated clocks
set_propagated_clock [all_clocks]

# Generating custom timing report
report_checks -path_delay min_max -fields {slew trans net cap input_pins} -format full_clock_expanded -digits 4

# Report hold skew
report_clock_skew -hold

# Report setup skew
report_clock_skew -setup

# Exit to OpenLANE flow
exit

# Checking current value of 'CTS_CLK_BUFFER_LIST'
echo $::env(CTS_CLK_BUFFER_LIST)

# Inserting 'sky130_fd_sc_hd__clkbuf_1' to first index of list
set ::env(CTS_CLK_BUFFER_LIST) [linsert $::env(CTS_CLK_BUFFER_LIST) 0 sky130_fd_sc_hd__clkbuf_1]

# Checking current value of 'CTS_CLK_BUFFER_LIST'
echo $::env(CTS_CLK_BUFFER_LIST)
```

Screenshots of commands run and timing report generated

<img width="1004" height="544" alt="image" src="https://github.com/user-attachments/assets/3bfb0803-71a3-4db3-bd46-e47e36f33c61" />
<img width="1001" height="543" alt="image" src="https://github.com/user-attachments/assets/df46f6bb-6a57-498e-a964-19391b4d5cf8" />
<img width="1001" height="549" alt="image" src="https://github.com/user-attachments/assets/ae8fb70d-49c6-4159-95e5-7c6963302789" />
<img width="989" height="544" alt="image" src="https://github.com/user-attachments/assets/83b6d7c4-ab08-438c-bb52-028205f46ff6" />
<img width="989" height="535" alt="image" src="https://github.com/user-attachments/assets/3c856f04-6811-416e-af09-5ec1e28fcc22" />
<img width="984" height="539" alt="image" src="https://github.com/user-attachments/assets/c36f43f2-a48e-42ea-aa15-403766ef3de3" />

</details>

## Day 5 - Final steps for RTL2GDS using tritonRoute and openSTA (25/03/2024 - 26/03/2024)

<details>
  <summary>
 THEORY
  </summary>

#### 1.ROUTING

<img width="1920" height="1080" alt="Screenshot (383)" src="https://github.com/user-attachments/assets/8781aa31-f59a-46a0-94c2-e5f02fcf4aab" />
<img width="1920" height="1080" alt="Screenshot (384)" src="https://github.com/user-attachments/assets/535b8566-13bd-49c9-9eaf-f19b838d0fe4" />
<img width="1920" height="1080" alt="Screenshot (385)" src="https://github.com/user-attachments/assets/8939060a-2afd-40c5-9e17-df3319ca0c4f" />

<img width="1920" height="1080" alt="Screenshot (386)" src="https://github.com/user-attachments/assets/90805716-02ac-4fe1-9fde-6cff5e874b05" />


(Some SS failed to upload)

</details>

  
<details>
  <summary>
 IMPLEMENTATION
  </summary>

* Day 5 tasks:-
1. Perform generation of Power Distribution Network (PDN) and explore the PDN layout.
2. Perfrom detailed routing using TritonRoute.
3. Post-Route parasitic extraction using SPEF extractor.
4. Post-Route OpenSTA timing analysis with the extracted parasitics of the route.

#### 1. Perform generation of Power Distribution Network (PDN) and explore the PDN layout.

Commands to perform all necessary stages up until now

```bash
# Change directory to openlane flow directory
cd Desktop/work/tools/openlane_working_dir/openlane

# alias docker='docker run -it -v $(pwd):/openLANE_flow -v $PDK_ROOT:$PDK_ROOT -e PDK_ROOT=$PDK_ROOT -u $(id -u $USER):$(id -g $USER) efabless/openlane:v0.21'
# Since we have aliased the long command to 'docker' we can invoke the OpenLANE flow docker sub-system by just running this command
docker
```
```tcl
# Now that we have entered the OpenLANE flow contained docker sub-system we can invoke the OpenLANE flow in the Interactive mode using the following command
./flow.tcl -interactive

# Now that OpenLANE flow is open we have to input the required packages for proper functionality of the OpenLANE flow
package require openlane 0.9

# Now the OpenLANE flow is ready to run any design and initially we have to prep the design creating some necessary files and directories for running a specific design which in our case is 'picorv32a'
prep -design picorv32a

# Addiitional commands to include newly added lef to openlane flow merged.lef
set lefs [glob $::env(DESIGN_DIR)/src/*.lef]
add_lefs -src $lefs

# Command to set new value for SYNTH_STRATEGY
set ::env(SYNTH_STRATEGY) "DELAY 3"

# Command to set new value for SYNTH_SIZING
set ::env(SYNTH_SIZING) 1

# Now that the design is prepped and ready, we can run synthesis using following command
run_synthesis

# Following commands are alltogather sourced in "run_floorplan" command
init_floorplan
place_io
tap_decap_or

# Now we are ready to run placement
run_placement

# Incase getting error
unset ::env(LIB_CTS)

# With placement done we are now ready to run CTS
run_cts

# Now that CTS is done we can do power distribution network
gen_pdn 
```

Screenshots of power distribution network run

<img width="1005" height="546" alt="image" src="https://github.com/user-attachments/assets/07a871d5-7a96-413c-8981-54e2bb50f709" />
<img width="1002" height="537" alt="image" src="https://github.com/user-attachments/assets/55e6122d-7280-44c2-9b6b-5b66e4bd0a92" />


Commands to load PDN def in magic in another terminal

```bash
# Change directory to path containing generated PDN def
cd Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/26-03_08-45/tmp/floorplan/

# Command to load the PDN def in magic tool
magic -T /home/vsduser/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged.lef def read 14-pdn.def &
```

Screenshots of PDN def

<img width="995" height="546" alt="image" src="https://github.com/user-attachments/assets/19fe4e20-7895-4c77-8829-5ca327399359" />
<img width="999" height="542" alt="image" src="https://github.com/user-attachments/assets/af8ad56c-dbbf-4f09-bd1d-39381a5dda3e" />
<img width="992" height="547" alt="image" src="https://github.com/user-attachments/assets/2f54ab61-11af-4f26-89b5-74032621b31e" />

#### 2. Perfrom detailed routing using TritonRoute and explore the routed layout.

Command to perform routing

```tcl
# Check value of 'CURRENT_DEF'
echo $::env(CURRENT_DEF)

# Check value of 'ROUTING_STRATEGY'
echo $::env(ROUTING_STRATEGY)

# Command for detailed route using TritonRoute
run_routing
```

Screenshots of routing run

<img width="998" height="550" alt="image" src="https://github.com/user-attachments/assets/77967a9a-040c-453f-a904-743e37a788cf" />
<img width="992" height="545" alt="image" src="https://github.com/user-attachments/assets/344689f1-7b23-4f8a-b070-991f49310788" />

<img width="996" height="551" alt="image" src="https://github.com/user-attachments/assets/4200f5c9-4a15-4701-8614-036c8544a56f" />


Commands to load routed def in magic in another terminal

```bash
# Change directory to path containing routed def
cd Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/26-03_08-45/results/routing/

# Command to load the routed def in magic tool
magic -T /home/vsduser/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged.lef def read picorv32a.def &
```

Screenshots of routed def

<img width="999" height="544" alt="image" src="https://github.com/user-attachments/assets/1c6e24e7-d572-4163-b83a-be7451700863" />
<img width="999" height="544" alt="image" src="https://github.com/user-attachments/assets/127d094a-02cb-4bfd-b6cd-8912af892373" />
<img width="995" height="552" alt="image" src="https://github.com/user-attachments/assets/95c37b60-fa33-4af7-928e-4341aec65753" />
<img width="990" height="545" alt="image" src="https://github.com/user-attachments/assets/e5636f05-84d0-46a9-b5ef-8464da8312b5" />

Screenshot of fast route guide present in `openlane/designs/picorv32a/runs/26-03_08-45/tmp/routing` directory

<img width="996" height="545" alt="image" src="https://github.com/user-attachments/assets/cecf7346-76af-4c09-8aae-7ccc70065957" />

#### 3. Post-Route parasitic extraction using SPEF extractor.

Commands for SPEF extraction using external tool

```bash
# Change directory
cd Desktop/work/tools/SPEF_EXTRACTOR

# Command extract spef
python3 main.py /home/vsduser/Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/26-03_08-45/tmp/merged.lef /home/vsduser/Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/26-03_08-45/results/routing/picorv32a.def
```

#### 4. Post-Route OpenSTA timing analysis with the extracted parasitics of the route.

Commands to be run in OpenLANE flow to do OpenROAD timing analysis with integrated OpenSTA in OpenROAD

```tcl
# Command to run OpenROAD tool
openroad

# Reading lef file
read_lef /openLANE_flow/designs/picorv32a/runs/26-03_08-45/tmp/merged.lef

# Reading def file
read_def /openLANE_flow/designs/picorv32a/runs/26-03_08-45/results/routing/picorv32a.def

# Creating an OpenROAD database to work with
write_db pico_route.db

# Loading the created database in OpenROAD
read_db pico_route.db

# Read netlist post CTS
read_verilog /openLANE_flow/designs/picorv32a/runs/26-03_08-45/results/synthesis/picorv32a.synthesis_preroute.v

# Read library for design
read_liberty $::env(LIB_SYNTH_COMPLETE)

# Link design and library
link_design picorv32a

# Read in the custom sdc we created
read_sdc /openLANE_flow/designs/picorv32a/src/my_base.sdc

# Setting all cloks as propagated clocks
set_propagated_clock [all_clocks]

# Read SPEF
read_spef /openLANE_flow/designs/picorv32a/runs/26-03_08-45/results/routing/picorv32a.spef

# Generating custom timing report
report_checks -path_delay min_max -fields {slew trans net cap input_pins} -format full_clock_expanded -digits 4

# Exit to OpenLANE flow
exit
```

Screenshots of commands run and timing report generated

<img width="1000" height="544" alt="image" src="https://github.com/user-attachments/assets/cf98f2a3-3756-4f6b-9b2d-d1d142c47dd8" />
<img width="984" height="551" alt="image" src="https://github.com/user-attachments/assets/6a1e0676-0ae7-4cab-9fc8-2c59ffdc29a1" />
<img width="996" height="541" alt="image" src="https://github.com/user-attachments/assets/ca176424-37b4-48f5-b0fd-e02fd6a49535" />
<img width="971" height="541" alt="image" src="https://github.com/user-attachments/assets/2d1de2c7-d0ed-441f-a11f-b86673c67a99" />



</details>



# Acknowledgements

* [Kunal Ghosh](https://github.com/kunalg123), Co-founder, VSD Corp. Pvt. Ltd.
* [Nickson P Jose](https://github.com/nickson-jose), Physical Design Engineer, Intel Corporation.
* [R. Timothy Edwards](https://github.com/RTimothyEdwards), Senior Vice President of Analog and Design, efabless Corporation.
















  
