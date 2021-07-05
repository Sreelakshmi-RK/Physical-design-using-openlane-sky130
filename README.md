

![image](https://user-images.githubusercontent.com/86832219/124394132-a2cafe80-dd1b-11eb-9594-e68e42d800ed.png)

## Contents
    
 ### Day 1: Inception of Open Source EDA ,OpenLane sky130PDK
 * Introduction
*  Physical Design
* Familiar with Openslane 
*  Openlane ASIC flow


 ### Day2 : Floorplan and Introduction to  library Cells
* Floorplan
* AspectRatio
* Preplaced cells
* Decoupling Capacitors

### Day 3: Library Cell design using Magic layout and Characterisation of Library Cell

* CMOS inverter ngspice simulations
* CMOS Fabrication Process
* Inception of Layout 
* Sky130A tech File Labs

### Day 4 : Pre-layout timing analysis and importance of good clock tree

* Delay tables and Timing Models
* ClockTreeSynthesis (CTS) using TritonCTS 
* Timing Analysis using OpenSTA

### Day 5: Routing and Power Distribution
* Lee_Maze Routing Algorithm
* Power Distribution
* Triton Route Features
***



       

         



## Day 1 :Inception of Open Source EDA ,OpenLane sky130PDK

**Introduction**
* Integrated circuit is the one in which thousand of gates ,resistors and capacitors are fabricated into it.An IC act as a memory,timer,counter ,amplifier etc.The main advantage of Ic is they are small in size and when comes to the functionality they does the best job.They are availabel in the form of packages.

![2](https://user-images.githubusercontent.com/86832219/124386693-37703500-dcf9-11eb-9964-5b14e419ec16.PNG)

In the above figure IP represents the Intellectual Property (IP) which are specific foundary. RISC V ,SRAM are the macros which are placed inside core.In the area surrounding the core I/O cells are placed. Physical design is the step which is used to place Intellectual Property (IP) and macros inside the core area.

**Physical design**
* Physical is the process of converting the circuit description which is written in HDL(Hardware Description Language) into a physical layout.It consists of different stages 
* Floorplan : In this macros are placed in the core area.
* Placement :In this standard cells are placed.
* Clock Tree Synthesis: In this clock tree is built.
* Routing: In this interconnections are made using metal layerrs and vias.
The IC communicates with hardware and the software .The system software converts the software language into assembly language which is the language understand by the IC and this way the required functionality is performed.

**OpenLane ASIC Flow**
* Openlane is an automated pandR tool which performs the RTS to GDS11 flow.  

![16](https://user-images.githubusercontent.com/86832219/124387622-f417c580-dcfc-11eb-9a9a-5b84a0b0a74c.PNG)


![17](https://user-images.githubusercontent.com/86832219/124390724-86729600-dd0a-11eb-81ed-78cf7eeda8ac.PNG)

![18](https://user-images.githubusercontent.com/86832219/124390752-98eccf80-dd0a-11eb-8b28-6bd7f3a1f0b9.PNG)

![19](https://user-images.githubusercontent.com/86832219/124390780-b28e1700-dd0a-11eb-9c2b-5bc641897da5.PNG)

![20](https://user-images.githubusercontent.com/86832219/124390789-bb7ee880-dd0a-11eb-9151-dd9b5b46fbe5.PNG)

![21](https://user-images.githubusercontent.com/86832219/124390810-d3566c80-dd0a-11eb-9442-bb4eb8249c72.PNG)

![22](https://user-images.githubusercontent.com/86832219/124390816-da7d7a80-dd0a-11eb-83db-04c7c529c1c1.PNG)

![24](https://user-images.githubusercontent.com/86832219/124390826-e701d300-dd0a-11eb-8ef8-620b610772b1.PNG)

![26](https://user-images.githubusercontent.com/86832219/124390836-fda82a00-dd0a-11eb-9eee-63f02e58a533.PNG)

![28](https://user-images.githubusercontent.com/86832219/124390844-0698fb80-dd0b-11eb-9ad0-9688707f35a6.PNG)

![29](https://user-images.githubusercontent.com/86832219/124390848-0dc00980-dd0b-11eb-9661-b707956b5acf.PNG)


* In order to invoke the design we use the following commands Linux terminal
`use docker commnad`
`use ./flow.tcl -interactive`


![docker](https://user-images.githubusercontent.com/86832219/124387978-3392e180-dcfe-11eb-9764-867d81b4c8f4.PNG)
Use the command prep -design design_name trial_run -overwrite
![image](https://user-images.githubusercontent.com/86832219/124391375-fa626d80-dd0d-11eb-8d2a-8f8057b37b08.png)

![image](https://user-images.githubusercontent.com/86832219/124391049-49a79e80-dd0c-11eb-982d-3f0205d92222.png)

![image](https://user-images.githubusercontent.com/86832219/124391151-d3576c00-dd0c-11eb-99c5-4c32296674c3.png) ![image](https://user-images.githubusercontent.com/86832219/124391348-d010b000-dd0d-11eb-9de5-5acf56f26888.png)

* The  percentage number of flops are obtained by dividing number of flops by total number of cells


**Synthesis :** Synthesis is the process of converting RTL code to optimised gate level netlist.It is obtained by using following command
`run_synthesis`

![image](https://user-images.githubusercontent.com/86832219/124391753-ba03ef00-dd0f-11eb-9d80-4366cfc7ff34.png)


***








 ## Day2 : Floorplan and Introduction to  library Cells

**Floorplan**
* It is the first step in the physical design.The quality of floorplan will decide the chip performance .It is the process of placing macros in the core area. It determines the size of the die and create wire tracks for placement of standard cells.
* **Core** :
* It is defined as the inner block which contains the std cells and macros.
* **Die**:
* It is the block around the core which contains i/o ports.
* **Aspect Ratio**:
* It wiil decide the size and shape of the chip.It is the ratio of vertical routing resources to the horizontal routing resources.If its value is 1 then it is of square shape and if it is greater than 1 then it is of rectangular shape.
> Aspect Ratio = Height / Width
* **Core Utilisation**:
*It defines the area occupied by macros,standard cells and other cells.If Core utilisation is 70% that means 70% of core area is use for placing the standard cells,macros and other cells and remaining 30% is for routing.In other words it is the area occupied by the netlist.
> Utilisation factor= Area occupied by the netlist /Total area of the core.

![image](https://user-images.githubusercontent.com/86832219/124381210-d471a480-dcde-11eb-897f-97ae7af54c1d.png)

**Preplaced cells:**
* These have user defined locationa and hence placed in chip before automated before automated placement and routing and this type of cells are called preplaced cells.Once they are placed on the core area they are not moved by any automated tools and the are fixed.Some of preplaced cells are mux,flipflop and comparator etc.

![image](https://user-images.githubusercontent.com/86832219/124381566-db99b200-dce0-11eb-827a-8c232499185c.png)

![image](https://user-images.githubusercontent.com/86832219/124381645-2287a780-dce1-11eb-80dc-1f166e477c0c.png)

**Decoupling Capacitors:**
* In order to protect the cells from the disturbances which occur in power supply deccouplig Capcitors are used.It is better to surround the macros using decoupling capacitors which are generally called as decap cells.

![image](https://user-images.githubusercontent.com/86832219/124381703-89a55c00-dce1-11eb-87fe-b57903277e66.png)

**Power Planning :** 
* The power planning is done in this stage. The power has to be distributed equally to all macros and standard cells using power network.

![image](https://user-images.githubusercontent.com/86832219/124381918-8068bf00-dce2-11eb-9770-fa593491bfb4.png)

**Pin Placement:**
* The pins are placed around the core.Clock ports are bigger in size when compared to other ports.Backend people decide the pin placement in Pnr flow.


![5](https://user-images.githubusercontent.com/86832219/124383659-3fc17380-dceb-11eb-8cd7-cf881eccfb01.PNG)

![51](https://user-images.githubusercontent.com/86832219/124383755-c7a77d80-dceb-11eb-848e-cf143cb5fd78.PNG)

![6](https://user-images.githubusercontent.com/86832219/124383671-4f40bc80-dceb-11eb-8dcb-0a7fdfd0d26f.PNG)


![image](https://user-images.githubusercontent.com/86832219/124383951-d5113780-dcec-11eb-8c7c-ae16f3d503de.png)


![image](https://user-images.githubusercontent.com/86832219/124384008-19043c80-dced-11eb-96e3-7551557bdad4.png)


![image](https://user-images.githubusercontent.com/86832219/124384073-5b2d7e00-dced-11eb-9466-8863e223b019.png)

* The floorplan is run by using the following command

`run_floorplan`

* The layout of the floorplan obtained can be seen by using  following command 
`magic -T`
![11](https://user-images.githubusercontent.com/86832219/124384784-88c7f680-dcf0-11eb-9bed-f5d076fac455.PNG)

![12](https://user-images.githubusercontent.com/86832219/124384794-9aa99980-dcf0-11eb-8e6c-99441d07db20.PNG)

![13](https://user-images.githubusercontent.com/86832219/124384814-a5642e80-dcf0-11eb-8b5f-a94955b8d813.PNG)

* To run placement use the following command

`run_placement`

![29](https://user-images.githubusercontent.com/86832219/124385102-fe809200-dcf1-11eb-8c21-2d612959dc53.PNG)

![place](https://user-images.githubusercontent.com/86832219/124385107-05a7a000-dcf2-11eb-9064-2b0c2d0825c7.PNG)
 
The standard cells can be seen by zooming the layout i.e., by select and press z. 

***
















 # Day 3: Library Cell design using Magic layout and Characterisation of Library Cell

**Spice deck**

* Spice deck is the one which gives information regarding the connectivity of components.In other words we can call this as netlist. 

**Component values**
* The components which are used are PMOS and NMOS.The width and length value of these play an important role in determining the output. The W and L values of PMOS and NMOS respectively are
> M1:PMOS W/L=0.375u / 0.25 
> M2 :NOMS W/L=0.375u / 0.25u 

**Node**
* A Node is a point where in between component is present. Node is a positive number starting from 0 to n.It can be either vdd,gnd,in,out.
The Model parameters and netlist description of PMOS and NMOS are as follows
PMOS:
Pre-layout and post-layout simulation
* M1 out in Vdd  Vdd  pmos W=0.375u L=0.25u
The above M1 represents PMOS which is connected in the specified order of drain gate source substrate.
NMOS:
* M2 out in 0  0  nmos  W=0.375u  L=0.25u
The above M1 represents NMOS which is connected in the specified order of drain gate source substrate.
* Cload out 0 10f
Here the load capacitor connected between the out and 0 node having a value of 10fF is specified in the above spice statement.
* Vdd vdd 0 2.5
Here also the power supply Vdd is connected between the vdd and 0 nodes and has value 2.5V is specified in the above spice statement.
Vin in 0 2.5
**Commands for simulating CMOS inverter**
* The following represents the commands for simulating spice model of CMOS inverter
* .op
* .dc Vin 0 2.5 0.05
* The spice which are mentioned above are used to sweep input voltage from 0 to 2.5v in steps of 0.05v to get the output voltage.
The following represents the cases of PMOS and NMOS where there is variation in waveform
* When, `Wn = Wp = 0.375u and Ln,p = 0.25u - The (W/L)n = (W/L)p = 1.5 `
*  The VTC Curve is shifted towards the left and the switching threshold Vm = 0.98 V
* When, `Wn = 0.375u, Wp= 0.9375 ( observe that Wp = 2.5 * Wn ) `
*  The VTC Curve is exactly at the middle , and the switching threshold Vm = 1.2 V
* Hence we can observe the transfer characteristics of CMOS inverter are as follows

![47](https://user-images.githubusercontent.com/86832219/124352341-58fbee80-dc1d-11eb-8d99-ab019968f754.PNG)  ![48](https://user-images.githubusercontent.com/86832219/124352493-feaf5d80-dc1d-11eb-808b-d041e93d5ba0.PNG)
# 
**Layout of CMOS inverter**
* The layout is drawn taking the connectivity information from netlist and Euler path has to be taken into consideration.The DRC rules have to be considered for drawing a layout.DRC is a foundary document which gives information about spacing,extension,overlap,contact size etc.
**CMOS Inverter characterisation**
* The characterisation of Inverter depends upon the following factors
* Derive actual dimensions for the function
* Script to create layout in Magic
* Final layout and input output * 

* The standard cell library is obtained into our design by cloning git repository
* The git link is as follows
* `https://github.com/nickson-jose/vsdstdcelldesign.git`

![image](https://user-images.githubusercontent.com/86832219/124353140-59e34f00-dc22-11eb-98cc-92ab75c2b5bc.png)

![vsdstdcelldesign](https://user-images.githubusercontent.com/86832219/124353066-c6aa1980-dc21-11eb-9c47-c10735813386.PNG)

* The tech file is copied using cp command

![image](https://user-images.githubusercontent.com/86832219/124354520-096fef80-dc2a-11eb-9442-7930b0445e55.png)

* The layout preview is obtained by using the below command

![50](https://user-images.githubusercontent.com/86832219/124355218-aaac7500-dc2d-11eb-8dcb-dafdb640b2a0.PNG)

*For central view of inverter layout press s and then v

![20](https://user-images.githubusercontent.com/86832219/124355301-fe1ec300-dc2d-11eb-90a8-d6d248589621.PNG)

* By using extract all an extracted file is generated. 

![19](https://user-images.githubusercontent.com/86832219/124355320-17c00a80-dc2e-11eb-8850-abbc3a930aff.PNG)

* By using ext2spice spice netlist is generated.

![image](https://user-images.githubusercontent.com/86832219/124355483-0cb9aa00-dc2f-11eb-9a7a-315eec19b86f.png)

* The extracted file is as below

![image](https://user-images.githubusercontent.com/86832219/124355989-75098b00-dc31-11eb-83d4-d30784357537.png)
* Modify using Escape+i

* The modified spice netlist is as below

![17](https://user-images.githubusercontent.com/86832219/124355724-5060e380-dc30-11eb-8bf0-ea470eab97b1.PNG)


![22](https://user-images.githubusercontent.com/86832219/124356217-7b4c3700-dc32-11eb-8465-799f7a4af6cb.PNG)


![21](https://user-images.githubusercontent.com/86832219/124356224-83a47200-dc32-11eb-97d9-7d95f0e84db2.PNG)


![25](https://user-images.githubusercontent.com/86832219/124356269-b9e1f180-dc32-11eb-9aa0-b64bb4c7260c.PNG)


![23](https://user-images.githubusercontent.com/86832219/124356257-a9ca1200-dc32-11eb-9a16-496d8a546584.PNG)


![24](https://user-images.githubusercontent.com/86832219/124356264-b0f12000-dc32-11eb-8030-d290e6b63aea.PNG)

       ***

# Day 4 : Pre-layout timing analysis and importance of good clock tree

**Setup time**: The time interval for which the data has to be stable before the clock edge is called setup time.

**Hold time** :The time interval for which the data has to be stable after the clock edge is called hold time.

**Skew**: The difference in the arrival of clock from clock source to clock pin of flipflops.The skew has to be as minimum as possible.Practically zero skew is not possible.

**Latency** :The amount of time taken to travel from clock source to clock definition point.

**Clock Jitter**: The variation of clock edge from the ideal clock edge is called jitter.It is modelled by using clock uncerrtainity.


**Clock Tree Synthesis:** CTS is the process of building the clock tree. Buffers and inverters are used for building the clock tree.The main aim of CTS is to minimise the clock skew. 

![cts](https://user-images.githubusercontent.com/86832219/124392580-208b0c00-dd14-11eb-9f4a-da5682ecb60a.PNG)

When u press g reference cell can be seen.

![33](https://user-images.githubusercontent.com/86832219/124392692-c179c700-dd14-11eb-95bf-60979113b4d0.PNG)

![35](https://user-images.githubusercontent.com/86832219/124392866-48c73a80-dd15-11eb-92bb-8fa0613c802e.PNG)

The information regarding tracks is  present in the track file which is mentioned below

![31](https://user-images.githubusercontent.com/86832219/124393239-14547e00-dd17-11eb-9b81-5569a6a6d97f.PNG)


![38](https://user-images.githubusercontent.com/86832219/124392872-5250a280-dd15-11eb-912a-a8d9fb6bd2d2.PNG)


![39](https://user-images.githubusercontent.com/86832219/124392888-6f857100-dd15-11eb-9b0f-9fe4b5ba899a.PNG)

![36](https://user-images.githubusercontent.com/86832219/124392939-afe4ef00-dd15-11eb-9054-ec341c65dc26.PNG)

![40](https://user-images.githubusercontent.com/86832219/124392960-d014ae00-dd15-11eb-8634-af1423ba270f.PNG)

![41](https://user-images.githubusercontent.com/86832219/124392967-d9057f80-dd15-11eb-86ba-00fb5e5e3535.PNG)

![42](https://user-images.githubusercontent.com/86832219/124392976-e15dba80-dd15-11eb-89da-c44defc25ca6.PNG)

![43](https://user-images.githubusercontent.com/86832219/124392986-ec184f80-dd15-11eb-99ec-5ca430292e8c.PNG)

The modified config.tcl is as below . It is modified using Esc+i.

![1](https://user-images.githubusercontent.com/86832219/124393370-d4da6180-dd17-11eb-9daa-a122d8a9e245.PNG)

![52](https://user-images.githubusercontent.com/86832219/124393420-0fdc9500-dd18-11eb-9b36-8cb675cadaf6.PNG)

![51](https://user-images.githubusercontent.com/86832219/124393425-1834d000-dd18-11eb-95a5-01bdc031d376.PNG)

![3](https://user-images.githubusercontent.com/86832219/124393441-2551bf00-dd18-11eb-8800-7837e1ea8677.PNG)

![2](https://user-images.githubusercontent.com/86832219/124393447-2d116380-dd18-11eb-9502-3001cec6134f.PNG)

Since the slack is met change the  strategy of synthesis, buffering, sizing to reduce the slack violations and run synthesis again.

After synthesis 

`run_placement`

![vsdstdcell](https://user-images.githubusercontent.com/86832219/124393820-f63c4d00-dd19-11eb-891f-4a5a1556d46c.PNG)  ![image](https://user-images.githubusercontent.com/86832219/124393024-1538e000-dd16-11eb-90c4-420b05865e38.png)










# Day 5: Routing and Power Distribution
***


**Routing** : The process of interconnecting the metal wire to all the cells  i.e., Macros,stdcells which are present in the core. Electrical connections using metals and vias are created in the layout, defined by the logical connections which are present in the netlist.Connections are made using vias for different metals.The main goal of routing is to reduce the total interconnect length.  
**Routing is of two types**

**Global Routing:**
* In Global Routing we dont do the actaul connections.The approximate interconnections between the blocks are made in this.In other words it just plan the connections .

**Detailed Routing:**
* Detailed routing takes information from global routing and does the actual interconnection between the cells. 


![image](https://user-images.githubusercontent.com/86832219/124377882-07f70380-dccc-11eb-9d0b-dc1a6832267e.png)

**Lees Algorithm**
* This is most widely used algorithm to find the path between two points.In this algorithm the cells between which the path has to be made are identified 
One cell is made target and other cell is made source. Routing grids are drawn on the chip .Numbering is done for the grid box  surrounding the cells.One has to continue to number the grid until target cell is reached. Based on this numbering the path is decided from source to target. Generally L shape routing is preferred. The main disadvantage of this algorithm is it consumes large amount of memory and time. 

![image](https://user-images.githubusercontent.com/86832219/124379794-af793380-dcd6-11eb-8173-bd2c11a77c38.png)    ![image](https://user-images.githubusercontent.com/86832219/124379801-b7d16e80-dcd6-11eb-88ee-942321a30cd7.png)

* The Command which used for routing is as below. Openlane uses Triton Route to do routing

`run_routing`

**Power Distribution**
* It is the process of distributing the power(VDD and VSS)  to all macros and standard cells which are present in the core.The power is distributed using rails,rings,straps.

* **Rails**  : The rails will connect VDD and VSS to std cells.
* **Rings**  : Ring is the one which is placed around the chip which Carries VDD and VSS.
* **Straps** :Since it is difficult to transfer power equally from edge of the chip to centre of the chip .We use vertical and horizontal nets in the chip from the rings to carry power.

![image](https://user-images.githubusercontent.com/86832219/124380506-835fb180-dcda-11eb-899c-0527002d05e6.png)

* The command which is used for generating power is as below

``gen_pdn
![gen](https://user-images.githubusercontent.com/86832219/124380547-d0dc1e80-dcda-11eb-9b33-583fabc94392.PNG)

![infopower](https://user-images.githubusercontent.com/86832219/124380555-d9ccf000-dcda-11eb-989d-2e91d552a7be.PNG)

![power](https://user-images.githubusercontent.com/86832219/124380558-e18c9480-dcda-11eb-8940-7db5242c12c0.PNG)


***

## Acknoweledge

Kunal Ghosh , Co-founder (VSD Corp. Pvt. Ltd).

Nickson Jose , VSD VLSI Engineer

Mansi Mahapatar VSD TA

MiliAnand  VSD TA








