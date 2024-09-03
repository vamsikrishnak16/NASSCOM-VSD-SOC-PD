# NASSCOM-VSD SOC Physical Design Training

#  RTL to GDSII flow using OpenLane

This training will guide you through the process of designing an Application Specific Integrated Circuit (ASIC) using the OpenLane ASIC flow. We will cover everything from the Register Transfer Level (RTL) design to generating the final Graphical Data System (GDS) file. The process involves several critical steps, starting with an RTL file and ending with a GDS file.

## Key Learnings

### RTL to GDS Flow

1. **End-to-End Process**:
   - Gained a comprehensive understanding of transforming a high-level hardware description into a physical ASIC layout.
   - Appreciated the significance of each stage in the flow, from synthesis to sign-off.

2. **Synthesis**:
   - Learned how RTL code is converted into a gate-level netlist using standard cell libraries.
   - Identified various cell views including Liberty, HDL, SPICE, and Layout.

3. **Floor and Power Planning**:
   - Understood the importance of floor planning for chip partitioning and I/O pad placement.

## Day 1

![image](https://github.com/user-attachments/assets/f2cfebff-40c1-4659-b5cb-abc5c2be2006)


## RISC-V Architecture

The RISC-V architecture is built on the principles of Reduced Instruction Set Computing (RISC) and is notable for being open-source, allowing anyone to design and implement a RISC-V CPU without paying licensing fees. This openness has created a collaborative environment, enabling contributions from a wide range of organizations, including both startups and industry leaders like Google and Intel.

A key characteristic of RISC-V is its modular design. The architecture includes a mandatory base ISA (Instruction Set Architecture) that can be extended with various optional components, allowing for customization based on specific application needs. For example, the RV32IMAC designation refers to a 32-bit CPU featuring the base integer ISA along with extensions for multiplication, atomic operations, and compressed instructions. This modularity enables developers to create CPUs that balance performance, power consumption, and complexity according to their requirements.

RISC-V is gaining widespread adoption across diverse industries such as cloud computing, automotive, and the Internet of Things (IoT). Companies are increasingly leveraging RISC-V to design custom chips optimized for specific tasks, like artificial intelligence and data processing. The architecture's adaptability and scalability make it ideal for a variety of devices, from high-performance servers to energy-efficient embedded systems. The RISC-V International organization, a nonprofit, governs the development and standardization of the RISC-V ISA. This group ensures that the architecture evolves with a focus on community-driven innovation rather than commercial interests, further solidifying its popularity within the tech community.

## Bridging Software Applications and Hardware

In everyday use, we interact with application software (apps) to control hardware devices. This interaction happens like this, Between the application software and the hardware, there is an intermediary layer known as system software. This layer acts as a bridge, converting application requests into a format that hardware can interpret, specifically binary language.

![image](https://github.com/user-attachments/assets/a9ec542f-278d-43fc-9428-095b3e4a264b)

- **Operating System (OS)**: The OS manages fundamental tasks such as input/output operations, memory management, and system-level functions. It also plays a crucial role in translating application software into machine-readable code in languages like C, C++, or Java.

- **Compiler**: The compiler processes the code generated by the OS and translates it into machine code or executable files (e.g., .exe files). This code is specifically designed to be executed on the hardware platform in use.

- **Assembler**: The assembler further converts these executable files into binary code. This binary code is the language that the hardware can interpret and execute to perform the required tasks.

# Overview of IC Design Elements and Terminology

## Core

The core is the central section of an integrated circuit (IC) where the essential logic functions are executed. It encompasses all combinational circuits as well as both soft and hard intellectual property (IP) blocks.

## Die

A die is the individual unit of semiconductor material that houses the core and the input/output (IO) pads. Multiple dies are manufactured on a single silicon wafer to optimize production efficiency.

## IO Pads

IO pads are the interface points that enable communication between the chip's core and the external environment. These pads include input, output, and power pads, facilitating the connection of the chip to other components.

## Intellectual Property (IP)

Foundry IPs are pre-designed circuit modules that can be reused across various designs. These may include elements like SRAM, ADCs, DACs, and PLLs, which often require custom design or human expertise.

## Process Design Kits (PDKs)

Process Design Kits (PDKs) act as a crucial link between design engineers and semiconductor fabrication plants. They contain essential files that model fabrication processes, including device models, design rule checks (DRC), layout versus schematic (LVS) checks, and standard cell libraries. For example, the SkyWater 130nm PDK is frequently used in IC design workshops.



# Overview of the RTL to GDSII Flow

The RTL to GDSII flow in VLSI design transforms an RTL (Register Transfer Level) description of a digital circuit into a physical layout prepared for manufacturing. This process includes several stages: RTL synthesis, floor planning, placement, routing, and ultimately generating the GDSII file format, which holds the layout data. Each stage ensures that the final integrated circuit (IC) layout accurately represents the intended functionality and adheres to fabrication standards.

## Specification and RTL Coding

The design process starts with a specification provided by the customer, detailing the required functionality of the chip. This specification is then converted into Register Transfer Level (RTL) code using Hardware Description Languages (HDL) such as Verilog or VHDL.

## Simulation and Verification

Once the RTL coding is complete, the design undergoes simulation to verify its functionality. This step ensures that the design operates as intended before moving to the next stage. Verification engineers thoroughly test the RTL code to identify and correct any bugs, ensuring the design's accuracy.

## Logic Synthesis

After successful verification, the RTL code is synthesized into a gate-level netlist. This involves translating the high-level design into an optimized format that can be implemented using standard cells from a technology library. Logic Equivalence Checking (LEC) is performed to confirm that the synthesized design retains the functionality of the original RTL code.

## Physical Design (Place and Route)

The physical design phase follows, encompassing floorplanning, placement, and routing of the netlist. This stage focuses on organizing the components on the silicon die, optimizing for area, and maintaining signal integrity. The final product of this phase is a GDSII file, the industry-standard format for layout data.

## Signoff and Tapeout

Before the design is sent for fabrication, it undergoes several signoff checks to ensure it meets all specifications and design rules. This final verification step is crucial for identifying any critical errors. Upon approval, the GDSII file is sent for fabrication, marking the tapeout phase and the completion of the design process.

![image](https://github.com/user-attachments/assets/53c70a9b-9f2b-47ab-8232-3b7ec3d96246)

## Importance of the RTL to GDSII Flow

The RTL to GDSII flow is vital for the following reasons:

- **Complexity Management**: It breaks down the complex chip design process into manageable stages, allowing for systematic development and verification.
- **Efficiency**: Automated tools for synthesis, verification, and layout significantly reduce the time required to move a chip from concept to production, typically within 6 to 24 months, depending on the design complexity.
- **Quality Assurance**: The flow includes multiple checks and validations to ensure that the final design meets high standards for performance and reliability.
- **Industry Relevance**: Mastery of the RTL to GDSII flow is essential for engineers in the semiconductor industry, as it encompasses the critical skills required for modern chip design and implementation.

#  Overview of OpenLane - Open-Source Digital ASIC Design

### Introduction

OpenLane has proven its effectiveness in real-world applications through successful tape-outs of RISC-V based SoCs. The project continues to advance, with significant enhancements in SystemVerilog support and user experience features in OpenLane 2.

### Purpose

OpenLane facilitates the transition from Register Transfer Level (RTL) design to GDSII layout, which is crucial for ASIC manufacturing. It is designed to address two primary use cases:
- **Macro Hardening**: Converting a macro from its HDL representation into a manufacturable layout.
- **SoC Integration**: Combining multiple macros into a cohesive System-on-a-Chip (SoC) design.

# OpenLANE ASIC Design Flow

The diagram below depicts the comprehensive ASIC design flow implemented in OpenLANE. The process starts with the Design RTL (Register Transfer Level), which is then synthesized into an optimized gate-level netlist using Yosys and ABC. This netlist is subsequently analyzed using Static Timing Analysis (STA) to identify any potential timing violations. Optionally, the flow can include Design for Test (DFT), utilizing the FAULT tool to enhance testability.

![image](https://github.com/user-attachments/assets/ea2a0188-3dd8-4378-ae46-e159f85a976f)


### Components

The OpenLane flow utilizes a range of open-source Electronic Design Automation (EDA) tools, including:
- **Yosys**: For synthesis
- **OpenROAD**: For placement and routing
- **Magic**: For layout editing
- **KLayout**: For layout viewing and verification

These tools work in concert to automate various stages of the ASIC design process, from synthesis to physical verification.


![image](https://github.com/user-attachments/assets/e3cf9c1d-e3b9-47e3-b18d-72dfb616b1b5)



### Versions

OpenLane is available in two main versions:
- **OpenLane 1**: A stable platform ideal for general ASIC designs, especially for multi-project wafer (MPW) programs.
- **OpenLane 2**: A more adaptable and customizable platform that supports user-defined ASIC implementation flows, making it suitable for complex designs.

## Features and Benefits

- **Automation**: OpenLane automates the complete ASIC design flow, allowing users to concentrate on design rather than tool integration complexities. This includes full automation of synthesis, placement, routing, and verification.
  
- **Customizability**: Users can create custom design flows using Python scripts, offering high flexibility for advanced design needs. This is especially valuable for users requiring specific functionalities not available in standard flows.

- **Open-Source Ecosystem**: OpenLane is part of the open-source ASIC design movement, aimed at democratizing access to advanced design tools and fostering collaboration and innovation within the design community.

## Use Cases

- **Macro Hardening**: This process converts HDL designs into manufacturable layouts, allowing for the reuse of hardened macros across different projects, thereby enhancing design efficiency and consistency.

- **SoC Integration**: OpenLane supports the integration of various macros into a complete chip design, which is crucial for developing complex SoCs that incorporate multiple functional blocks.

# RTL2GDS OpenLANE ASIC Flow: Practical Implementation

## Day 1 Labs

### Linux Command Basics

1. **pwd**: Displays the current working directory path.
2. **ls**: Lists all files and directories in the current location.
3. **cd**: Navigate between directories within the directory tree.
4. **mkdir**: Creates a new directory.
5. **rmdir**: Deletes an empty directory.
6. **rm**: Removes files or directories.
7. **cp**: Copies files or directories.
8. **mv**: Moves or renames files or directories.
9. **cat**: Displays the contents of a file.
10. **clear**: Clears the terminal screen.
11. **help**: Provides information on the usage of other commands.

### File extensions and their Purpose

  - **libs.ref**: Contains design libraries essential for the ASIC flow.
  - **lef**: Library Exchange Format files describing cell layouts.
  - **lib**: Liberty files used for timing and power analysis.
  - **gds**: GDSII files containing the graphical layout of cells.
  - **verilog**: Verilog models for simulation and design verification.
  - **libs.tech**: Technology files tailored for EDA tools.
  - **magic**: Files specific to Magic layout tool.
  - **klayout**: KLayout technology files and layer properties.
  - **ngspice**: SPICE models for circuit simulations.
  - **openroad**: Configuration files for OpenROAD flow.
  - **drc**: Design Rule Check files.
  - **lvs**: Layout Versus Schematic check files.
  - **pex**: Parasitic Extraction files.

## Flowchart for running synthesis in OpenLane

![image](https://github.com/user-attachments/assets/28c7a0db-320a-4083-b461-03a93f7a7365)


### Proceed with the steps outlined

To start working with OpenLane, open your terminal and navigate to the following directory:

     cd /Desktop/work/tools/openlane_working_dir/openlane

#### Running OpenLane in Docker

Execute the following alias to run OpenLane in Docker:

     docker


![Screenshot 2024-08-29 121716](https://github.com/user-attachments/assets/44931662-412a-442e-97f6-0ed8344321fb)


To start the tool in interactive mode, execute the following command:

`bash`

./flow.tcl -interactive

To import the required package and prepare the design, execute the command below:

    package require openlane 0.9
    prep -design picorv32a

![Screenshot 2024-08-29 123504](https://github.com/user-attachments/assets/73d536fc-c0a1-45ba-8031-c84ab22cb9f3)

## Directory Structure

Once the preparation process is complete, a new directory, named with the current date, will be created inside the `runs` folder. This directory will contain all the required subdirectories for storing results, reports, and other relevant data. A new directory structure will be set up to organize the design files, with subdirectories designated for different components like results and reports.


- **src**: Includes Verilog files and a constraints file
- **LEF Merging**:
  The technology LEF (.tlef) and cell LEF (.lef) files are merged into a single format. The technology LEF contains layer information (e.g., metal layers), while the cell LEF includes cell information.

- **Design Placement**:
  All design-related files are placed under the `designs` directory to ensure they are well-organized and accessible for subsequent steps.

## Synthesis

To run the synthesis process, execute the following command:

     run_synthesis

![Screenshot 2024-08-29 125343](https://github.com/user-attachments/assets/49b71c39-0429-4573-9f14-b370c70c5fe1)

![Screenshot 2024-08-29 130042](https://github.com/user-attachments/assets/a255c5d0-2d70-45bc-bc2a-a0059b451c89)

![Screenshot 2024-08-29 130109](https://github.com/user-attachments/assets/b7e2b6b5-bf4d-4607-814b-d9b33a2a7a56)


## Day 2

## FloorPlan and Placement

### Chip Floorplanning Considerations

### Utilization Factor and Aspect Ratio

To determine the Utilization Factor and Aspect Ratio, we first need to understand how to define the height and width of the core and die areas.

- **Core**: The core area of a chip is where all the logic cells and components are placed. It is essentially the functional part of the chip.

- **Die**: The die area surrounds the core and is used for placing I/O-related components.

The dimensions of the core area are determined by the netlist of the design, which specifies the number and types of components needed. The height and width of the die area depend on the core area’s dimensions.

For example, if a netlist includes two logic gates and two flip-flops, each with an area of 1 square unit, the netlist comprises four elements. Therefore, the minimum total area required for the core will be 4 square units.

### Utilization Factor

The Utilization Factor is defined as the ratio of the core area occupied by the netlist to the total core area. For an effective floor plan, the Utilization Factor should be less than 1. A Utilization Factor of 1 indicates that the core area is fully utilized, leaving no room for additional logic, which is typically undesirable.

`Utilization Factor = (Area occupied by netlist / Total core area)`

### Aspect Ratio

The Aspect Ratio is the ratio of the core's height to its width. An Aspect Ratio of 1 signifies that the core is square-shaped, while a ratio other than 1 indicates a rectangular core.

`Aspect Ratio = (Height of the core / Width of the core)`

![image](https://github.com/user-attachments/assets/fa393d9b-ec3d-4060-bfe8-162736a9e373)

In this example, the calculations are as follows:

- **Utilization Factor**: (4 squnits)/(4 squnits) = 1

- **Aspect Ratio**: (2 units)/(2 units) = 1

   *Note: The core is square in shape.*

![image](https://github.com/user-attachments/assets/30016e8a-fc19-438d-8943-91b6834e2919)

In this example, the calculations are as follows:

- **Utilization Factor**: (4 squnits)/(8 squnits) = 0.5

- **Aspect Ratio**: (2 units)/(4 units) = 0.5

   *Note: The core is rectangular in shape.*

## Flowchart for running floorplan in OpenLane

![image](https://github.com/user-attachments/assets/09e3819d-bf1b-42f1-9787-682824eb50bf)

### Floorplan Configuration

To ensure the floorplan runs smoothly, designers need to manage specific settings that impact the floorplan's configuration. For instance, parameters like the utilization factor and aspect ratio are critical switches that affect the floorplan. It is essential for designers to verify these settings before initializing the floorplan to ensure they align with the project's requirements. The image below illustrates the various switches available during the floorplan stage.

To run the floorplan process, execute the following command:

    run_floorplan

![Screenshot 2024-08-29 184258](https://github.com/user-attachments/assets/84e3469a-35f6-4809-b4e0-959b71423829)

![Screenshot 2024-08-29 184328](https://github.com/user-attachments/assets/8a11683b-b171-4c5e-9864-2ed027044e25)

## Floorplan Layout Review in Magic

After completing the floorplan, you can evaluate the generated report to analyze aspects like die area. For graphical visualization of the design, open the MAGIC tool by executing the code:

     Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/29-08_07-04/results/floorplan$ magic -T /home/vsduser/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged.lef def read picorv32a.floorplan.def &

![Screenshot 2024-08-29 185321](https://github.com/user-attachments/assets/d431d535-c40f-4020-b70c-73675b711a53)

![Screenshot 2024-08-29 190224](https://github.com/user-attachments/assets/d4f3150a-a5e5-4895-908a-1222d10eefab)

![Screenshot 2024-08-29 190323](https://github.com/user-attachments/assets/e74742ab-c6c8-497f-817a-c6ae759db84e)

### Aligning the Design:

1. Press `S` to select the entire design.
2. Press `V` to vertically center the design on the screen.

### Zooming into a Specific Area:

1. Click and drag to select the desired region.
2. Right-click to open the context menu.
3. Press `Z` to zoom into the selected area.

### Viewing Cell Details:

1. Position your cursor over the cell of interest.
2. Press `S` to select the cell.
3. In the `tkcon` window, type the command `what` to view details of the selected cell.

![Screenshot 2024-08-29 200900](https://github.com/user-attachments/assets/a1a385db-7560-481f-b68a-cd2559684f0b)

## Placement

Placement is a critical step in VLSI (Very Large Scale Integration) design, involving the assignment of physical positions to standard cells or logic elements within a chip or block. Here’s an overview:

1. **Global Placement:**
   - In this phase, general positions are assigned to movable objects (cells).
   - Some overlap between objects is permissible at this stage.
   - The objective is to create an approximate layout that meets area requirements.

2. **Detailed Placement:**
   - This phase refines the positions established during global placement.
   - It ensures that no overlaps occur and that cells are placed on valid sites.
   - The quality of detailed placement is crucial as it affects the efficiency of the subsequent routing process.

### Process Design Kits (PDKs)

A Process Design Kit (PDK) is a detailed collection of files provided by semiconductor foundries that outlines the fabrication process for integrated circuits. These kits are essential for the design process, offering technology-specific details that designers use to create, simulate, and verify their designs before moving to manufacturing. PDKs are crucial for ensuring that designs are feasible for production and meet performance standards. A precise PDK significantly enhances the chances of first-pass success in silicon fabrication, which is key to minimizing time-to-market and development costs.

### Key Components of PDKs

- **Device Libraries**: PDKs include libraries of primitive devices such as transistors, capacitors, resistors, and other essential components for circuit design.
  
- **Design Rules**: They provide design rule checking (DRC) guidelines to ensure that the layout meets the manufacturing capabilities of the foundry. This includes requirements for minimum feature sizes, spacing, and other geometric constraints.
  
- **PCells**: Parameterized cells (PCells) are part of PDKs, enabling designers to create complex layouts that automatically adjust according to specified parameters.
  
- **Verification Tools**: PDKs include verification tools like LVS (Layout Versus Schematic) to ensure that the layout matches the schematic.
  
- **Modeling and Simulation**: PDKs contain simulation models (e.g., SPICE models) that predict the behavior of the designed circuits under different conditions.
  
- **Documentation**: Comprehensive documentation is provided to assist designers in using the PDK, including design rule manuals and technology data.

### Design Rule Check (DRC) and Layout vs. Schematic (LVS) Rules

### Design Rule Check (DRC)

Design Rule Check (DRC) is a crucial verification stage in the circuit design process. It ensures that the physical layout of the circuit adheres to the manufacturing constraints specified in the Process Design Kit (PDK). DRC rules help identify potential issues such as:

- Minimum spacing between components
- Widths of metal lines
- Area requirements for specific features

By applying DRC rules, designers can detect and correct errors early in the design process, thereby avoiding expensive modifications and revisions later on.

### Layout vs. Schematic (LVS)

Layout vs. Schematic (LVS) is a crucial verification step that ensures the circuit layout aligns with the original schematic design. The LVS process involves:

- Comparing the netlist derived from the layout with the netlist from the schematic.
- Verifying that all connections and components are accurately represented in both the layout and the schematic.

LVS is essential for confirming that the final design will operate as intended once fabricated, thereby reducing the risk of functional failures in the manufactured chips.


## Placement Configuration in OpenLane

Placement configuration in OpenLane requires setting parameters that define how design elements are positioned within the chip layout. Important parameters include target density, maximum allowable displacement for cell placement, and configurations for macro placement. These settings are crucial for optimizing the layout to enhance both performance and area efficiency.

To run the placement process, execute the following command:

    run_placement

![Screenshot 2024-08-30 093108](https://github.com/user-attachments/assets/7e9448a7-a1bf-4aff-bf15-f60df313c7a5)

## Placement Layout Review in Magic

After completing the placement, you can have the graphical visualization of the design in the MAGIC tool. Open the MAGIC tool by executing the code:

     /Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/29-08_07-04/results/placement$ magic -T /home/vsduser/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged.lef def read picorv32a.placement.def &

![Screenshot 2024-08-30 093321](https://github.com/user-attachments/assets/e1ea47bc-a444-492a-ad1f-158f33508ebf)

### Outputs

- **GDSII:** The layout file in GDSII format, used for fabrication.
- **Spice Extracted Netlist:** Contains parasitic information for accurate circuit simulation.
- **LEF (Library Exchange Format):** Provides details about cell sizes, pin locations, and other essential information.
- **Timing, Noise, and Power Libraries:** Generated during the characterization process.
- **CDL (Circuit Description Language):** A textual representation of the circuit.

## Day 3

## Design library cell using Magic Layout and ngspice characterization

### Creating a Standard Cell Layout

1. **Design the Inverter Layout:**
   - Utilize a layout tool (such as MAGIC) to draft the inverter layout.
   - Adhere to process-specific design rules and guidelines.
   - Position standard cells (transistors, metal layers, etc.) according to the logical schematic.

2. **Extraction Process:**
   - After completing the layout, extract parasitic capacitances and resistances.
   - In the `tkcon` window, run the command `extract all`.
   - This action generates an extracted file containing parasitic details (e.g., capacitances, interconnect resistance).
   - The extracted file will be saved in the `vsdstdcelldesign` directory.

3. **SPICE Netlist:**
   - Use the extracted data to assemble a SPICE-compatible netlist (typically in `.sp` or `.cir` format).
   - Incorporate transistor models, capacitances, and resistances.
   - This netlist will be used for simulations in tools like ngspice.

### Introduction to LEF Files in VLSI Design

LEF (Library Exchange Format) files are crucial for interfacing between layout tools and place-and-route (PnR) tools in VLSI (Very Large Scale Integration) design.

#### Purpose of LEF Files

- **Layout Abstraction:**
  - LEF files provide an abstract representation of a block, such as a macro or a standard cell, containing only the essential details required for PnR tools.
- **Essential Information:**
  - Instead of the entire layout, PnR tools need minimal information, including the PR boundary (bounding box) and pin positions.

## LEF Files

### Technology LEF
Contains details about the metal layers, vias, and DRC (Design Rule Check) technology used by the placer and router.

### Cell LEF
Provides an abstract view of the cell, including information about the placement and routing (PR) boundary, pin positions, and metal layer details.

## Inverter Characterization with Sky130 Model Files

This lab focuses on characterizing an inverter using `ngspice` and Sky130 model files. The objective is to extract essential parameters from the simulation results.

 [vsdstdcelldesign](https://github.com/nickson-jose/vsdstdcelldesign) layout view of cmos inverter in MAGIC tool


![Screenshot 2024-08-31 111906](https://github.com/user-attachments/assets/e52dd281-0d1a-4054-86f7-bfa3e19f5ebc)


### Extracting Parasitics and Characterizing the Cell Design

To extract parasitics and characterize the cell design, use the following commands in the `tkcon` window:

    extract all
    ext2spice cthresh 0 rthresh 0
    ext2spice

![Screenshot 2024-08-31 143643](https://github.com/user-attachments/assets/533b74c3-bd8c-45b0-9d51-f0eda36700ee)

![Screenshot 2024-08-31 143902](https://github.com/user-attachments/assets/a2ded976-37ae-4761-b8df-213b5ec65bea)

![Screenshot 2024-08-31 163734](https://github.com/user-attachments/assets/3c1ee6cc-4de8-45b3-9ca6-3e46d5e8e39c)




Install ngspice tool by using the command in the openlane terminal

     sudo apt-get install ngspice 

The next step is to execute the SPICE file using the ngspice tool with the following command:

     ngspice sky130_inv.spice

![Screenshot 2024-08-31 170900](https://github.com/user-attachments/assets/131cdf1e-2f0c-49cf-b8e9-6058f7b6363f)

![Screenshot 2024-08-31 171025](https://github.com/user-attachments/assets/ddccb894-b503-4b19-bbb4-c180303dc83b)

### CMOS Inverter Simulation with ngspice

This guide covers the creation of a basic CMOS inverter netlist and the execution of DC and transient analyses using ngspice. You will learn how to evaluate key static and dynamic characteristics of the inverter.

#### Static Characteristics

1. **Switching Threshold (Vth):**
   - The voltage level at which the inverter shifts from a high state (logic 1) to a low state (logic 0).
2. **Input High Voltage (Vih):**
   - The minimum input voltage recognized as logic 1.
3. **Input Low Voltage (Vil):**
   - The maximum input voltage recognized as logic 0.
4. **Output High Voltage (Voh):**
   - The voltage at which the output switches from low to high.
5. **Output Low Voltage (Vol):**
   - The voltage at which the output switches from high to low.
6. **Noise Margins:**
   - The voltage ranges between Vil and Vol (low noise margin) and between Vih and Voh (high noise margin).

#### Dynamic Characteristics

1. **Propagation Delays:**
   - The duration it takes for the output to respond to an input change.
2. **Rise Time (tr):**
   - The time required for the output to rise from Vol to Voh.
3. **Fall Time (tf):**
   - The time required for the output to fall from Voh to Vol.

### Parameters to Characterize

1. **Rise Time:**
   - The time taken for the output waveform to transition from 20% to 80% of its maximum value.
   - Using data points:
     - x0 = 2.16422e-09, y0 = 0.660027
     - x1 = 2.20608e-09, y1 = 2.64019
   - Rise time = x1 - x0 = 0.0418 ns

![Screenshot 2024-09-01 112109](https://github.com/user-attachments/assets/a2b66377-4aa9-4613-b3a4-e5076038468b)


2. **Fall Time:**
   - The time taken for the output waveform to transition from 80% to 20% of its maximum value.
   - Using data points:
     - x0 = 4.04121e-09, y0 = 2.64021
     - x1 = 4.06923e-09, y1 = 0.66
   - Fall time = x1 - x0 = 0.0280 ns

![Screenshot 2024-09-01 112606](https://github.com/user-attachments/assets/acbfb8ab-5599-4263-9aca-a6e3235d2390)

3. **Propagation Delay:**
   - The time taken for a 50% transition at the output (0 to 1) corresponding to a 50% transition at the input (1 to 0).
   - Using data points:
     - x0 = 2.14577e-09, y0 = 1.64533
     - x1 = 2.18604e-09, y1 = 1.65
   - Propagation delay = x1 - x0 = 0.04027 ns

### LEF File Generation
After successfully characterizing the inverter, the next step is to generate a LEF (Library Exchange Format) file.

wget http://opencircuitdesign.com/open_pdks/archive/drc_tests.tgz


**VLSI Layout Geometries and DRC Errors**

This section examines various layout geometries (M3.1, M3.2, M3.5, and M3.6) and identifies the specific DRC (Design Rule Check) errors linked with each:

1. **M3.1 (Metal Width DRC):**
   - Error: The metal width does not comply with design rules.
   - Violation: The width of the metal trace in M3.1 falls below the minimum specified threshold.

2. **M3.2 (Metal Spacing DRC):**
   - Error: Metal spacing violation detected.
   - Violation: The spacing between adjacent metal traces in M3.2 does not meet the required minimum distance.

3. **M3.5 (Via Overlapping DRC):**
   - Error: Overlapping vias issue.
   - Violation: Vias in M3.5 are overlapping, which is not allowed per design rules.

4. **M3.6 (Minimum Area DRC):**
   - Error: Minimum area violation.
   - Violation: The enclosed area within M3.6 is below the specified minimum area requirement.

open the Magic tool with the command

     magic -d XR
