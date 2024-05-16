## SIMULATION AND IMPLEMENTATION OF  COMBINATIONAL LOGIC CIRCUITS

### AIM: 
 To simulate and synthesis ENCODER, DECODER, MULTIPLEXER, DEMULTIPLEXER, MAGNITUDE COMPARATOR using Vivado 2023.2.

### APPARATUS REQUIRED:
VIVADO 2023.2
### PROCEDURE:
STEP:1 Start the Vivado, Select and Name the New project.<br>
STEP:2 Select the device family, device, package and speed. <br>
STEP:3 Select new source in the New Project and select Verilog Module as the Source type.<br>
STEP:4 Type the File Name and Click Next and then finish button. Type the code and save it.<br>
STEP:5 Select the Behavioural Simulation in the Source Window and click the check syntax.<br>
STEP:6 Click the simulation to simulate the program and give the inputs and verify the outputs as per the truth table.

### ENCODER
### LOGIC DIAGRAM
![321167032-fc152017-5a98-4379-ad05-9d5b51464f95](https://github.com/Krishnakumar284/VLSI-LAB-EXP-2/assets/160303010/60ad3c69-f3e1-4e2c-9eda-607add1244b2)
### VERILOG CODE:
```
module encoder_8 3(d,a,b,c) ;
input [7:0]d;
output a,b,c;
or(a,d[4],d[5],d[6],d[7]);
or(b,d[2],d[3],d[6],d[7]);
or(c,d[1],d[3],d[5],d[7]);
endmodule
```
### OUTPUT:
![321167446-183347dd-2f89-4b2b-af9a-c512b9f91cb4](https://github.com/Krishnakumar284/VLSI-LAB-EXP-2/assets/160303010/e4ff99e6-5abe-4f5f-886c-632b69317196)

### DECODER
### LOGIC DIAGRAM:
![321167658-33f14baa-a617-45ad-8583-88428b86eeb4](https://github.com/Krishnakumar284/VLSI-LAB-EXP-2/assets/160303010/ec306eba-cc22-439a-9aa9-ef09f0ced0e5)
### VERILOG CODE:
```
module decoder_8(a,b,c,y);
input a,b,c; 
output[7:0]y; 
and gl(y[0],(~a),(~b),(~c)); 
and g2(y[1],(~a),(~b),(c)); 
and g3(y[2],(~a),(b),(~c));
and g4(y[3],(~a),(b),(c));
and g5(y[4],(a),(~b),(~c));
and g6(y[5],(a), (~b), (c));
and g7(y[6], (a), (b), (~c)); 
and g8(y[7], (a), (b), (c));
endmodule
```
### OUTPUT:
![321168398-0009daf3-b87b-421e-bf51-19a0acd16ffd](https://github.com/Krishnakumar284/VLSI-LAB-EXP-2/assets/160303010/aa223828-7878-45e5-92c6-e3d8836032fd)

## MULTIPLEXER
### LOGIC DIAGRAM:
![321168608-eefa8e2f-6117-4854-819c-1eacf903e2cb](https://github.com/Krishnakumar284/VLSI-LAB-EXP-2/assets/160303010/eb20954e-cdd1-48a6-9fb0-3c186e78df08)

### VERILOG CODE:
```
module mux(a,b,c,d,s0,s1,y);
input a,b,c,d,s0,s1;
output y;
assign y=s1 ?(s0?d:c):(s0?b:a);
endmodule
```
### OUTPUT:
![321169046-4c4b8891-37a6-4900-9758-031e1c5cbc0a](https://github.com/Krishnakumar284/VLSI-LAB-EXP-2/assets/160303010/d802d599-38f7-451a-9ea7-88037ab7c0d7)

### DEMULTIPLEXER
### LOGIC DIAGRAM:
![321169394-cc70b515-a956-4edb-a61b-816aaef1d168](https://github.com/Krishnakumar284/VLSI-LAB-EXP-2/assets/160303010/7489416c-151a-45c3-b09c-c6e700b9021a)

### VERILOG CODE:
```
module Demultiplexer(in,s0,s1,s2,d0,d1,d2,d3,d4,d5,d6,d7);
input in,s0,s1,s2;
output d0,d1,d2,d3,d4,d5,d6,d7;
assign d0=(in & ~s2 & ~s1 &~s0),
d1=(in & ~s2 & ~s1 &s0),
d2=(in & ~s2 & s1 &~s0),
d3=(in & ~s2 & s1 &s0),
d4=(in & s2 & ~s1 &~s0),
d5=(in & s2 & ~s1 &s0),
d6=(in & s2 & s1 &~s0),
d7=(in & s2 & s1 &s0);
endmodule
```
### OUTPUT:
![321169654-6ed1777a-624d-4310-91d7-9a15f65977d9](https://github.com/Krishnakumar284/VLSI-LAB-EXP-2/assets/160303010/cc2e48ea-ed88-499c-872b-1e6962ae4625)

## MAGNITUDE COMPARATOR
### LOGIC DIAGRAM:
![321169924-bc01a976-d517-4aaa-9b48-3de231bfb658](https://github.com/Krishnakumar284/VLSI-LAB-EXP-2/assets/160303010/c6108e91-ed2a-4ce3-85d5-3bc30ba60caf)

### VERILOG CODE:
```
module magcomp(a,b,l,g,e);
input [3:0]a,b;
output reg l,g,e;
always @(*)
begin
if(a>b)
begin
     l=1'b0;
     g=1'b1;
     e=1'b0;
end
else if(a<b)
begin
     l=1'b1;
     g=1'b0;
     e=1'b0;
end
else
begin
     l=1'b0;
     g=1'b0;
     e=1'b1;
end
end
endmodule
```
### OUTPUT:
![321170169-3772b5ec-ad51-471d-a9f3-61771db81722](https://github.com/Krishnakumar284/VLSI-LAB-EXP-2/assets/160303010/5800f5c9-eb13-4f1d-a4b6-f4770159af56)

## RESULT:
 Hence ENCODER, DECODER, MULTIPLEXER, DEMULTIPLEXER, MAGNITUDE COMPARATOR are simulated and synthesised using Vivado 2023.2.
