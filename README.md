# SIMULATION AND IMPLEMENTATION OF LOGIC GATES, ADDERS AND SUBTRACTORS
**AIM:**<br>

&emsp;&emsp;To simulate and implement Logic Gates,Adders and Subtractor using VIVADO 2023.2.<br>

**APPARATUS REQUIRED:**<br>

&emsp;&emsp;VIVADO 2023.2<br>

**PROCEDURE:**<br>

 STEP:1 Launch the Vivado 2023.2 software.<br>
 STEP:2 Click on “create project ” from the starting page of vivado.<br>
 STEP:3 Choose the design entry method:RTL(verilog/VHDL).<br>
 STEP:4 Crete design source and give name to it and click finish.<br>
 STEP:5 Write the verilog code and check the syntax.<br>
 STEP:6 Click “run simulation” in the navigator window and click “Run behavioral simulation”.<br>
 STEP:7 Verify the output in the simulation window.<br>

**LOGIC DIAGRAM:**<br>

**LOGIC GATES:**

![image](https://github.com/navaneethans/VLSI-LAB-EXPERIMENTS/assets/6987778/ee17970c-3ac9-4603-881b-88e2825f41a4)


**HALF ADDER:**

![image](https://github.com/navaneethans/VLSI-LAB-EXPERIMENTS/assets/6987778/0e1ecb96-0c25-4556-832b-aeeedfdfe7b9)


**FULL ADDER:**

![image](https://github.com/navaneethans/VLSI-LAB-EXPERIMENTS/assets/6987778/9bb3964c-438f-469d-a3de-c1cca6f323fb)


**HALF SUBTRACTOR:**

![image](https://github.com/navaneethans/VLSI-LAB-EXPERIMENTS/assets/6987778/731470b7-eb4e-49f8-8bb7-2994052a7184)



**FULL SUBTRACTOR:**

![image](https://github.com/navaneethans/VLSI-LAB-EXPERIMENTS/assets/6987778/d66f874b-c1f2-44b3-a035-7149b56430c1)



**8 BIT RIPPLE CARRY ADDER:**

![image](https://github.com/navaneethans/VLSI-LAB-EXPERIMENTS/assets/6987778/7385a408-40a5-4203-8050-b72818622d79)



**VERILOG CODE:**<br>

**LOGIC GATES:**<br>

 module logicgate(a,b,andgate,orgate,nandgate,norgate,xorgate,xnorgate,notgate);<br>
 input a,b;<br>
 output andgate,orgate,nandgate,norgate,xorgate,xnorgate,notgate;<br>
 and(andgate,a,b);<br>
 or(orgate,a,b);<br>
 nand(nandgate,a,b);<br>
 nor(norgate,a,b);<br>
 xor(xorgate,a,b);<br>
 xnor(xnorgate,a,b);<br>
 not(notgate,a);<br>
 endmodule<br>

**HALF ADDER:**<br>

 module half_adder(a,b,sum,carry);<br>
 input a,b;<br>
 output sum,carry;<br>
 xor g1(sum,a,b);<br>
 and g2(carry,a,b);<br>
 endmodule<br>

**FULL ADDER:**<br>

 module fulladder(a,b,c,sum,carry);<br>
 input a,b,c;<br>
 output sum,carry;<br>
 wire w1,w2,w3;<br>
 xor(w1,a,b);<br>
 xor(sum,w1,c);<br>
 and(w2,w1,c);<br>
 and(w3,a,b);<br>
 or(carry,w2,w3);<br>
 endmodule<br>

**HALF SUBTRACTOR:**<br>

 module halfsub(a,b,diff,borrow);<br>
 input a,b;<br>
 output diff,borrow;<br>
 xor(diff,a,b);<br>
 and(borrow,~a,b);<br>
 endmodule<br>

**FULL SUBTRACTOR:**<br>

 module fs(a,b,bin,d,bout);<br>
 input a,b,bin;<br>
 output d,bout;<br>
 wire w1,w2,w3;<br>
 xor(w1,a,b);<br>
 xor(d,w1,bin);<br>
 and(w2,~a,b);<br>
 and(w3,~w1,bin);<br>
 or(bout,w3,w2);<br>
 endmodule<br>

**8 BIT RIPPLE CARRY ADDER:**<br>

 module fulladder(a,b,c,sum,carry);<br>
 input a,b,c;<br>
 output sum,carry;<br>
 wire w1,w2,w3;<br>
 xor(w1,a,b);<br>
 xor(sum,w1,c);<br>
 and(w2,w1,c);<br>
 and(w3,a,b);<br>
 or(carry,w2,w3);<br>
 endmodule<br>
 
 module rca_8bit(a,b,cin,s,cout);<br>
 input [7:0]a,b;<br>
 input cin;<br>
 output [7:0]s;<br>
 output cout;<br>
 wire [7:1]w;<br>
 fulladder f1(a[0], b[0], cin, s[0], w[1]);<br>
 fulladder f2(a[1], b[1], w[1], s[1], w[2]);<br>
 fulladder f3(a[2], b[2], w[2], s[2], w[3]);<br>
 fulladder f4(a[3], b[3], w[3], s[3], w[4]);<br>
 fulladder f5(a[4], b[4], w[4], s[4], w[5]);<br>
 fulladder f6(a[5], b[5], w[5], s[5], w[6]);<br>
 fulladder f7(a[6], b[6], w[6], s[6], w[7]);<br>
 fulladder f8(a[7], b[7], w[7], s[7], cout);<br>
 endmodule<br>

**OUTPUT:**

**LOGIC GATES:**

![logicgates](https://github.com/TharunPR/VLSI-LAB-EXP-1/assets/117915125/2019027f-3d2e-4488-b17e-57c8850a59e1)

**HALF ADDER:**

![halfadd](https://github.com/TharunPR/VLSI-LAB-EXP-1/assets/117915125/221aebf9-0ffa-474c-930f-743cc98d02cc)

**FULL ADDER:**

![fulladd](https://github.com/TharunPR/VLSI-LAB-EXP-1/assets/117915125/7bd02df3-47ba-4638-bb8c-43f1c6b124f0)

**HALF SUBTRACTOR:**

![halfsub](https://github.com/TharunPR/VLSI-LAB-EXP-1/assets/117915125/eab80fcb-9d88-4c5c-a0b5-c581a3fdc433)

**FULL SUBTRACTOR:**

![fullsub](https://github.com/TharunPR/VLSI-LAB-EXP-1/assets/117915125/1b1ca532-1483-45b5-bbab-611467188435)

**8 BIT RIPPLE CARRY ADDER:**

![8_bit_rca](https://github.com/TharunPR/VLSI-LAB-EXP-1/assets/117915125/0ffba1da-ff70-4649-90c5-ad0730f90a30)

**RESULT:**<br>
&emsp;&emsp;Thus the simulation and implementation of Logic Gates, Adders and Subtractors is done and outputs are verified.

