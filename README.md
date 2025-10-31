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







</details>



<details>
  <summary>
 IMPLEMENTATION
  </summary>









</details>


















  
