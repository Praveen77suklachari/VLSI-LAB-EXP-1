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

----Type Verilog Code #VERILOG CODE:

Program
Logic Gates:
```
module logicgate (a,b,andgate,orgate,xorgate,nandgate,norgate,xnorgate,notgate);
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
Half Adder:
```
module halfadder(a,b,sum,carry);
input a,b;
output sum,carry;
xor g1(sum,a,b);
and g2(carry,a,b);
endmodule
```
Half Subractor:
```
module halfsubtractor(a,b,diff,borrow);
input a,b;
output diff,borrow;
xor g1(diff,a,b);
and g2(borrow,~a,b);
endmodule
```
Full Adder:
```
module fadd(a,b,c,sum,carry);
input a,b,c;
output sum,carry;
wire w1,w2,w3;
xor g1(w1,a,b);
and g2(w2,a,b);
xor g3(sum,w1,c);
and g4(w3,w1,c);
or g5(carry,w3,w2);
endmodule
```
Full Subtractor:
```
module fs(a,b,bin,d,bout);
input a,b,bin; 
output d,bout;
wire w1,w2,w3;
xor g1(w1,b,bin; 
xor g2(d,w1,a);
and g3(w2,a,~w1);
and g4(w3,~b,bin);
or g5(bout,w2,w3);
endmodule
```
4 bit ripple carry adder:
```
module rippe_adder(S,Cout,X,Y,Cin);
input [3:0] X,Y;
input Cin;
output [3:0] S;
output Cout;
wire w1,w2,w3;
fulladder u1(S[0],w1,X[0],Y[0],Cin);
fulladder u2(S[1],w2,X[1],Y[1],w1);
fulladder u3(S[2],w3,X[2],Y[2],w2);
fulladder u4(S[3],Cout,X[3],Y[3],w3);
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
8 bit ripple carry adder:
```
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
OUTPUT:

-----Place a Waveform Generated from Xilinx ISE

OR GATE:
![316397848-4b503d63-b2c0-4255-a581-b6b273081b5c](https://github.com/PoornaTkD/VLSI-LAB-EXP-1/assets/95264589/c8979ba3-13fc-4a26-ad78-d55fec310637)
NOT gate:
![316398615-3f6a703e-3557-40d3-8934-f6fda5d413c4](https://github.com/PoornaTkD/VLSI-LAB-EXP-1/assets/95264589/46d8bdc5-ae45-4b55-88db-732ab24d46ca)
AND GATE :
![316399127-15897bb4-d7d3-48d8-ba32-0ca3b6fb188e](https://github.com/PoornaTkD/VLSI-LAB-EXP-1/assets/95264589/9144a71d-e880-4572-974f-4b274a8b7fee)
NAND GATE:
![316399253-0753d13c-aeae-4f34-a0ad-c3f18b783204](https://github.com/PoornaTkD/VLSI-LAB-EXP-1/assets/95264589/b2e0dd22-8017-4227-9818-0c0bddef9629)
NOR GATE:
![316399338-f728e8e9-d8c5-4985-9270-cd5998745696](https://github.com/PoornaTkD/VLSI-LAB-EXP-1/assets/95264589/66e99028-fbb6-4b45-a9cc-cae291918ef6)
XNOR:
![316399404-439a0925-ff55-406a-acb6-3bcb28fe9b80](https://github.com/PoornaTkD/VLSI-LAB-EXP-1/assets/95264589/78731a15-653a-48b9-acce-29aa256ae8aa)
XOR:
![316399489-870121a2-8dc6-4f59-a1cc-ce04c2235b78](https://github.com/PoornaTkD/VLSI-LAB-EXP-1/assets/95264589/9c52918e-4097-411c-b26f-2d061a1c5138)
HALF ADDER:
![316399555-8de4e914-6118-4ccf-868e-88dd08a09d7d](https://github.com/PoornaTkD/VLSI-LAB-EXP-1/assets/95264589/9f5cc3db-0f7b-4fa4-9d05-56383b865250)
HALF SUBTRACTOR:
![316399758-d335eb66-f012-4d35-9a14-35157d8b3129](https://github.com/PoornaTkD/VLSI-LAB-EXP-1/assets/95264589/ea57d0cc-cbe3-4394-ae64-5ba9cdc9ab96)
FULL SUBTRACTOR:
![316400009-35839a9b-53a8-43ed-8b3b-cc889a1c6ea6](https://github.com/PoornaTkD/VLSI-LAB-EXP-1/assets/95264589/764261fc-46cd-42a0-abed-cfb7284408d3)
4 BIT RIPPLE CARRY ADDERR:
![316400109-67b67b05-3429-4a0e-abda-e1c1305a4f82](https://github.com/PoornaTkD/VLSI-LAB-EXP-1/assets/95264589/9f128aa6-c3eb-4d95-9572-a58673f032eb)
8 BIT RIPPLE CARRY ADDER:
![316400175-6cf32583-d6ca-4bd2-890e-6948b0cd67a4](https://github.com/PoornaTkD/VLSI-LAB-EXP-1/assets/95264589/16172438-5c6a-4d56-90dc-0b1639dbee2c)
RESULT: 
Hence Logic Gates,Adders and Subtractor are simulated and synthesised using Vivado 2023.2.



