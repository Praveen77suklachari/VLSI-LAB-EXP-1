# VLSI-LAB-EXPERIMENTS
AIM: To simulate and synthesis Logic Gates,Adders and Subtractor using Xilinx ISE.

APPARATUS REQUIRED: Xilinx 14.7 Spartan6 FPGA

PROCEDURE: STEP:1 Start the Xilinx navigator, Select and Name the New project. STEP:2 Select the device family, device, package and speed. STEP:3 Select new source in the New Project and select Verilog Module as the Source type. STEP:4 Type the File Name and Click Next and then finish button. Type the code and save it. STEP:5 Select the Behavioral Simulation in the Source Window and click the check syntax. STEP:6 Click the simulation to simulate the program and give the inputs and verify the outputs as per the truth table. STEP:7 Select the Implementation in the Sources Window and select the required file in the Processes Window. STEP:8 Select Check Syntax from the Synthesize XST Process. Double Click in the Floorplan Area/IO/Logic-Post Synthesis process in the User Constraints process group. UCF(User constraint File) is obtained. STEP:9 In the Design Object List Window, enter the pin location for each pin in the Loc column Select save from the File menu. STEP:10 Double click on the Implement Design and double click on the Generate Programming File to create a bitstream of the design.(.v) file is converted into .bit file here. STEP:12 Load the Bit file into the SPARTAN 6 FPGA STEP:11 On the board, by giving required input, the LEDs starts to glow light, indicating the output.

Logic Diagram :

Logic Gates:
![image](https://github.com/navaneethans/VLSI-LAB-EXPERIMENTS/assets/6987778/ee17970c-3ac9-4603-881b-88e2825f41a4)


Half Adder:

![image](https://github.com/navaneethans/VLSI-LAB-EXPERIMENTS/assets/6987778/0e1ecb96-0c25-4556-832b-aeeedfdfe7b9)


Full adder:

![image](https://github.com/navaneethans/VLSI-LAB-EXPERIMENTS/assets/6987778/9bb3964c-438f-469d-a3de-c1cca6f323fb)


Half Subtractor:

![image](https://github.com/navaneethans/VLSI-LAB-EXPERIMENTS/assets/6987778/731470b7-eb4e-49f8-8bb7-2994052a7184)



Full Subtractor:

![image](https://github.com/navaneethans/VLSI-LAB-EXPERIMENTS/assets/6987778/d66f874b-c1f2-44b3-a035-7149b56430c1)



8 Bit Ripple Carry Adder

![image](https://github.com/navaneethans/VLSI-LAB-EXPERIMENTS/assets/6987778/7385a408-40a5-4203-8050-b72818622d79)



VERILOG CODE:

#1:-
FULL_ADDER:-
```
module fulladder(sum,cout, a,b,c);
input a,b,c;
output sum,cout;
  wire w1,w2,w3,w4,w5;
  xor x1(w1,a,b);
  xor x2(sum,w1,c);  
  and a1(w2,a,b);
  and a2(w3,b,c);
  and a3(w4,a,c);
  
  or o1(w5,w2,w3);
  or o2(cout,w5,w4);
    
endmodule
```

OUTPUT:
simulation:
![image](https://github.com/Praveen77suklachari/VLSI-LAB-EXP-1/assets/124765056/916e5047-a437-4a50-8232-49fa1ccd7b83)
Elobrated Design:
![image](https://github.com/Praveen77suklachari/VLSI-LAB-EXP-1/assets/124765056/84dcaac8-896f-4c86-8c47-5c7b03d96599)
#2:-

FULL_SUBTRACTOR:-
```
// fullsubtractor using gate level modeling
module full_sub(borrow,diff,a,b,c);
output borrow,diff;
input a,b,c;
wire w1,w4,w5,w6;
xor (diff,a,b,c);
not n1(w1,a);
and a1(w4,w1,b);
and a2(w5,w1,c);
and a3(w6,b,c);
or o1(borrow,w4,w5,w6);
endmodule
```
output
Simulation:
![image](https://github.com/Praveen77suklachari/VLSI-LAB-EXP-1/assets/124765056/abe9fe78-ebff-49a9-895d-c58178d18802)
Eaborated Design:
![image](https://github.com/Praveen77suklachari/VLSI-LAB-EXP-1/assets/124765056/2e29cfbb-c45b-4b00-80fc-8495d4d9adc5)
#3:-

HALF_ADDER:
```
module half_adder(a,b,sum,carry);
input a,b;
output sum,carry; // sum and carry
or(sum,a,b);
and(carry,a,b);
endmodule
```
OUTPUT:-

Simulation:
![image](https://github.com/Praveen77suklachari/VLSI-LAB-EXP-1/assets/124765056/43a02454-5e1e-4183-93d3-5dd7cdf479e3)
Elaborated Design:
![image](https://github.com/Praveen77suklachari/VLSI-LAB-EXP-1/assets/124765056/ea5d2619-e573-4569-b8f7-0c938b6b95dd)
#4 HALF_SUBTRACTOR:-
```
module halfsubtractor( D,Bo,A,B);
input A,B;
output D,Bo;
wire w1;
xor (D,A,B);
not (w1,B);
and (Bo,B,w1);
endmodule
```
OUTPUT:-

Simulation:

![image](https://github.com/Praveen77suklachari/VLSI-LAB-EXP-1/assets/124765056/69520379-b81c-4035-9967-4d786da26d0d)
Elaborated Design:
![image](https://github.com/Praveen77suklachari/VLSI-LAB-EXP-1/assets/124765056/d54692a9-957a-43aa-ae80-9b291c6abf15)
#5 LOGIC_GATES:
```
module logicgates(a,b,andgate,orgate,xorgate,nandgate,norgate,xnorgate,notgate);
input a,b;
output andgate,orgate,xorgate,nandgate,norgate,xnorgate,notgate;
and(andgate,a,b);
or(orgate,a,b);
xor(xorgate,a,b);
nand(nandgate,a,b);  
nor(norgate,a,b);
xnor(xnorgate,a,b);
not(notgate,a);
endmodule
```
OUTPUT:

Simulation:

![image](https://github.com/Praveen77suklachari/VLSI-LAB-EXP-1/assets/124765056/d98f573b-1d6a-4157-91bf-f6d9ecca99ec)
Elaborated Design:
![image](https://github.com/Praveen77suklachari/VLSI-LAB-EXP-1/assets/124765056/d3d29324-1cda-4699-a1aa-1f6e92fb1b5c)
#6

RIPPLE_CARRY_Adder(4-BIT):-
```

module rippe_adder(S, Cout, X, Y,Cin);
input [3:0] X, Y;// Two 4-bit inputs
input Cin;
output [3:0] S;
output Cout;
wire wl, w2, w3;

fulladder u1(S[0], w1,X[0], Y[0], Cin);
fulladder u2(S[1], w2,X[1], Y[1], w1);
fulladder u3(S[2], w3,X[2], Y[2], w2);
fulladder u4(S[3], Cout,X[3], Y[3], w3);
endmodule
module fulladder(S, Co, X, Y, Ci);
input X, Y, Ci;
output S, Co;
wire w1,w2,w3;
//Structural code for one bit full adder 
xor G1(wl, X, Y);
xor G2(S, w1, Ci);
and G3(w2, w1, Ci);
and G4(w3, X, Y);
or  G5(Co, w2, w3);
endmodule
```
OUTPUT:-

Simulation: 
![image](https://github.com/Praveen77suklachari/VLSI-LAB-EXP-1/assets/124765056/2791a816-7a03-4ab0-b995-aef9258324c2)
Elaborated Design:
![image](https://github.com/Praveen77suklachari/VLSI-LAB-EXP-1/assets/124765056/53a0a86f-0d09-4403-8299-cdd04a166b42)
#7

RIPPLE_CARRY_ADDER(8-BIT):-
```

module fulladder(sum,cout, a,b,c);
input a,b,c;
output sum,cout;
  wire w1,w2,w3,w4,w5;
  xor x1(w1,a,b);
  xor x2(sum,w1,c);  
  and a1(w2,a,b);
  and a2(w3,b,c);
  and a3(w4,a,c);
  
  or o1(w5,w2,w3);
  or o2(cout,w5,w4);
    
endmodule
module rippe_adder(S,Cout,X,Y,Cin);
input [7:0] X,Y;
input Cin;
output [7:0] S;
output Cout;
wire w1,w2,w3,w4,w5,w6,w7;
fulladder u1(S[0],w1,X[0],Y[0],Cin);
fulladder u2(S[1],w2,X[1],Y[1],w1);
fulladder u3(S[2],w3,X[2],Y[2],w2);
fulladder u4(S[3],w4,X[3],Y[3],w3);
fulladder u5(S[4],w5,X[4],Y[4],w4);
fulladder u6(S[5],w6,X[5],Y[5],w5);
fulladder u7(S[6],w7,X[6],Y[6],w6);
fulladder u8(S[7],Cout,X[7],Y[7],w7);
endmodule

module fulladder(S,CO,X,Y,Ci);
input X,Y,Ci;
output S,CO;
wire w1,w2,w3;
xor G1(w1,X,Y);
xor G2(S,w1,Ci);
and G3(w2,X,Ci);
and G4(w3,X,Y);
or G5(CO,w3,w3);
endmodule
```
OUTPUT:-

Simulation:
![image](https://github.com/Praveen77suklachari/VLSI-LAB-EXP-1/assets/124765056/a534d73f-05f8-4672-acaf-39211d80bf42)
Elaborated Design:
![image](https://github.com/Praveen77suklachari/VLSI-LAB-EXP-1/assets/124765056/2a32cd82-e525-4023-abf7-223c5e27c955)



RESULT:

