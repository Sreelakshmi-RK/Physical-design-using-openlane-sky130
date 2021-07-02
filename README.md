<h1>Day 3 Design library cell using Magic Layout and ngspice characterization</h1>
1.	Spice deck
Spice deck is the one which gives information regarding the connectivity of components.In other words we can call this as netlist.
Component values
The components which are used are PMOS and NMOS.The width and length value of these play an important role in determining the output. The W and L values of PMOS and NMOS respectively are
M1:PMOS
W/L=0.375u / 0.25
M2 :NOMS
W/L=0.375u / 0.25u
Node:
A Node is a point where in between component is present. Node is a positive number starting from 0 to n.It can be either vdd,gnd. 

