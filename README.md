# SIMULATION AND IMPLEMENTATION OF LOGIC GATES, ADDERS AND SUBTRACTORS
**AIM:**<br>

&emsp;&emsp;To simulate and implement the following circuits using VIVADO 2023.2.<br>

&emsp;&emsp;&emsp;&emsp;&emsp;1) Logic Gates<br>
&emsp;&emsp;&emsp;&emsp;&emsp;2) Adders<br>
&emsp;&emsp;&emsp;&emsp;&emsp;3) Subtractors<br>

**SOFTWARE REQUIRED:**<br>

&emsp;&emsp;VIVADO 2023.2<br>

**PROCEDURE:**<br>

 STEP:1 Launch the Vivado 2023.2 software.<br>
 STEP:2 Click on “create project ” from the starting page of vivado.<br>
 STEP:3 Choose the design entry method:RTL(verilog/VHDL).<br>
 STEP:4 Crete design source and give name to it and click finish.<br>
 STEP:5 Write the verilog code and check the syntax.<br>
 STEP:6 Click “run simulation” in the navigator window and click “Run behavioral simulation”.<br>
 STEP:7 Verify the output in the simulation window.<br>

**LOGIC GATES:**

**LOGIC DIAGRAM:**

![image](https://github.com/navaneethans/VLSI-LAB-EXPERIMENTS/assets/6987778/ee17970c-3ac9-4603-881b-88e2825f41a4)

**VERILOG CODE:**

 ```
 module logicgate(a,b,andgate,orgate,nandgate,norgate,xorgate,xnorgate,notgate);
 input a,b;
 output andgate,orgate,nandgate,norgate,xorgate,xnorgate,notgate;
 and(andgate,a,b);
 or(orgate,a,b);
 nand(nandgate,a,b);
 nor(norgate,a,b);
 xor(xorgate,a,b);
 xnor(xnorgate,a,b);
 not(notgate,a);
 endmodule
```

**OUTPUT:**

![logicgates](https://github.com/TharunPR/VLSI-LAB-EXP-1/assets/117915125/2019027f-3d2e-4488-b17e-57c8850a59e1)


**HALF ADDER:**

**LOGIC DIAGRAM:**

![image](https://github.com/navaneethans/VLSI-LAB-EXPERIMENTS/assets/6987778/0e1ecb96-0c25-4556-832b-aeeedfdfe7b9)

**VERILOG CODE:**

```
 module half_adder(a,b,sum,carry);
 input a,b;
 output sum,carry;
 xor g1(sum,a,b);
 and g2(carry,a,b);
 endmodule
 ```

**OUTPUT:**

![halfadd](https://github.com/TharunPR/VLSI-LAB-EXP-1/assets/117915125/221aebf9-0ffa-474c-930f-743cc98d02cc)

**FULL ADDER:**

**LOGIC DIAGRAM:**

![image](https://github.com/navaneethans/VLSI-LAB-EXPERIMENTS/assets/6987778/9bb3964c-438f-469d-a3de-c1cca6f323fb)

**VERILOG CODE:**

```
 module fulladder(a,b,c,sum,carry);
 input a,b,c;
 output sum,carry;
 wire w1,w2,w3;
 xor(w1,a,b);
 xor(sum,w1,c);
 and(w2,w1,c);
 and(w3,a,b);
 or(carry,w2,w3);
 endmodule
```

**OUTPUT:**

![fulladd](https://github.com/TharunPR/VLSI-LAB-EXP-1/assets/117915125/7bd02df3-47ba-4638-bb8c-43f1c6b124f0)

**HALF SUBTRACTOR:**

**LOGIC DIAGRAM:**

![image](https://github.com/navaneethans/VLSI-LAB-EXPERIMENTS/assets/6987778/731470b7-eb4e-49f8-8bb7-2994052a7184)

**VERILOG CODE:**

```
 module halfsub(a,b,diff,borrow);
 input a,b;
 output diff,borrow;
 xor(diff,a,b);
 and(borrow,~a,b);
 endmodule
```

**OUTPUT:**

![halfsub](https://github.com/TharunPR/VLSI-LAB-EXP-1/assets/117915125/eab80fcb-9d88-4c5c-a0b5-c581a3fdc433)


**FULL SUBTRACTOR:**

**LOGIC DIAGRAM:**

![image](https://github.com/navaneethans/VLSI-LAB-EXPERIMENTS/assets/6987778/d66f874b-c1f2-44b3-a035-7149b56430c1)

**VERILOG CODE:**

```
 module fs(a,b,bin,d,bout);
 input a,b,bin;
 output d,bout;
 wire w1,w2,w3;
 xor(w1,a,b);
 xor(d,w1,bin);
 and(w2,~a,b);
 and(w3,~w1,bin);
 or(bout,w3,w2);
 endmodule
```

**OUTPUT:**

![fullsub](https://github.com/TharunPR/VLSI-LAB-EXP-1/assets/117915125/1b1ca532-1483-45b5-bbab-611467188435)

**8 BIT RIPPLE CARRY ADDER:**

**LOGIC DIAGRAM:**

![image](https://github.com/navaneethans/VLSI-LAB-EXPERIMENTS/assets/6987778/7385a408-40a5-4203-8050-b72818622d79)

**VERILOG CODE:**

```
 module fulladder(a,b,c,sum,carry);
 input a,b,c;
 output sum,carry;
 wire w1,w2,w3;
 xor(w1,a,b);
 xor(sum,w1,c);
 and(w2,w1,c);
 and(w3,a,b);
 or(carry,w2,w3);
 endmodule
 
 module rca_8bit(a,b,cin,s,cout);
 input [7:0]a,b;
 input cin;
 output [7:0]s;
 output cout;
 wire [7:1]w;
 fulladder f1(a[0], b[0], cin, s[0], w[1]);
 fulladder f2(a[1], b[1], w[1], s[1], w[2]);
 fulladder f3(a[2], b[2], w[2], s[2], w[3]);
 fulladder f4(a[3], b[3], w[3], s[3], w[4]);
 fulladder f5(a[4], b[4], w[4], s[4], w[5]);
 fulladder f6(a[5], b[5], w[5], s[5], w[6]);
 fulladder f7(a[6], b[6], w[6], s[6], w[7]);
 fulladder f8(a[7], b[7], w[7], s[7], cout);
 endmodule
```
**OUTPUT:**

![8_bit_rca](https://github.com/TharunPR/VLSI-LAB-EXP-1/assets/117915125/0ffba1da-ff70-4649-90c5-ad0730f90a30)

**RESULT:**<br>
&emsp;&emsp;Thus the simulation and implementation of Logic Gates, Adders and Subtractors is done and outputs are verified.

