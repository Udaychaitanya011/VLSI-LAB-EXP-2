EXP-2

Date:

                  SIMULATION AND IMPLEMENTATION OF COMBINATIONAL LOGIC CIRCUITS

AIM:
 To simulate and synthesis ENCODER, DECODER, MULTIPLEXER, DEMULTIPLEXER, MAGNITUDE COMPARATOR using VIVADO 2023.2

APPARATUS REQUIRED: 

VIVADO 2023.2

PROCEDURE:

STEP:1 Launch the Vivado 2023.2 software.

STEP:2 Click on “create project ” from the starting page of vivado.

STEP:3 Choose the design entry method:RTL(verilog/VHDL).

STEP:4 Crete design source and give name to it and click finish.

STEP:5 Write the verilog code and check the syntax.

STEP:6 Click “run simulation” in the navigator window and click “Run behavioral simulation”.

STEP:7 Verify the output in the simulation window.

LOGIC DIAGRAM

ENCODER
![331344105-cbdf6539-bfb9-4526-aedb-0f06358dfca5](https://github.com/Udaychaitanya011/VLSI-LAB-EXP-2/assets/161430397/4c6ced98-23b7-4280-abfb-8687124c5219)


verilog code
```
module encoder(a,y);
input [7:0]a;
output[2:0]y;
or(y[2],a[6],a[5],a[4],a[3]);
or(y[1],a[6],a[5],a[2],a[1]);
or(y[0],a[6],a[4],a[2],a[0]);
endmodule
```
output

![331344041-bb3e066b-ee2d-4b13-86b4-76d69a71f2dc](https://github.com/Udaychaitanya011/VLSI-LAB-EXP-2/assets/161430397/d4ae55b1-ef3f-47c2-aa5f-6a0711158dc4)

LOGIC DIAGRAM DECODER

![331343984-2027ff6a-4b37-4e65-b26c-bb721b2e2970](https://github.com/Udaychaitanya011/VLSI-LAB-EXP-2/assets/161430397/e2f81b2b-b4e6-4888-ad05-353a846985d9)


verilog code
```
module decoder1(a,y);
input [2:0]a;
output[7:0]y;
and(y[0],~a[2],~a[1],~a[0]);
and(y[1],~a[2],~a[1],a[0]);
and(y[2],~a[2],a[1],~a[0]);
and(y[3],~a[2],a[1],a[0]);
and(y[4],a[2],~a[1],~a[0]);
and(y[5],a[2],~a[1],a[0]);
and(y[6],a[2],a[1],~a[0]);
and(y[7],a[2],a[1],a[0]);
endmodule
```
output
![331343944-df7019a2-8450-472e-b032-10915d08063c](https://github.com/Udaychaitanya011/VLSI-LAB-EXP-2/assets/161430397/db92d907-a04b-4ff0-8d03-4bfcd5ec19bc)


LOGIC DIAGRAM MULTIPLEXER

![331343911-c5d0e39c-a235-4dc2-be61-019b84136e3a](https://github.com/Udaychaitanya011/VLSI-LAB-EXP-2/assets/161430397/c9512139-7bb6-4dca-bfaa-d28323044278)


VERILOG CODE
```
module mux(s,c,a);
input [2:0]s;
input [7:0]a;
wire [7:0]w;
output c;
and(w[0],a[0],~s[2],~s[1],~s[0]);
and(w[1],a[1],~s[2],~s[1],s[0]);
and(w[2],a[2],~s[2],s[1],~s[0]);
and(w[3],a[3],~s[2],s[1],s[0]);
and(w[4],a[4],s[2],~s[1],~s[0]);
and(w[5],a[5],s[2],~s[1],s[0]);
and(w[6],a[6],s[2],s[1],~s[0]);
and(w[7],a[7],s[2],s[1],s[0]);
or (c,w[0],w[1],w[2],w[3],w[4],w[5],w[6],w[7]);
endmodule
```
output

![331343726-639cdb5d-6fec-40a3-bb41-877b66690ba5](https://github.com/Udaychaitanya011/VLSI-LAB-EXP-2/assets/161430397/804c467d-0dc8-4115-90ce-32f8b7d65df5)

VERILOG CODE DEMULTIPLEXER
![331343670-bd6a85c3-0d1f-49e2-9380-32c6bc22913b](https://github.com/Udaychaitanya011/VLSI-LAB-EXP-2/assets/161430397/d3602d4d-d42e-402a-96e5-5a24b6e160a2)



VERILOG CODE
```
module demux_8(s,a,y);
input [2:0]s;
input a;
output [7:0]y;
and(y[0],a,~s[2],~s[1],~s[0]);
and(y[1],a,~s[2],~s[1],s[0]);
and(y[2],a,~s[2],s[1],~s[0]);
and(y[3],a,~s[2],s[1],s[0]);
and(y[4],a,s[2],~s[1],~s[0]);
and(y[5],a,s[2],~s[1],s[0]);
and(y[6],a,s[2],s[1],~s[0]);
and(y[7],a,s[2],s[1],s[0]);
endmodule
```

output
![331343634-7278ac37-d30b-4678-b6f3-d3e74ecf902e](https://github.com/Udaychaitanya011/VLSI-LAB-EXP-2/assets/161430397/43ecf731-a33e-4fd7-a3fa-2b45d98d8c04)


MAGNITUDE COMPARATOR

![331343617-be421dba-bd82-470d-8437-7824cdc767c0](https://github.com/Udaychaitanya011/VLSI-LAB-EXP-2/assets/161430397/351260d9-4ecf-411d-adcb-9d55f7209a46)

VERILOG CODE
```
module comparator(a,b,eq,lt,gt);
input [3:0] a,b;
output reg eq,lt,gt;
always @(a,b)
begin
 if (a==b)
 begin
  eq = 1'b1;
  lt = 1'b0;
  gt = 1'b0;
 end
 else if (a>b)
 begin
  eq = 1'b0;
  lt = 1'b0;
  gt = 1'b1;
 end
 else
 begin
  eq = 1'b0;
  lt = 1'b1;
  gt = 1'b0;
 end
end 
endmodule
```
OUTPUT
![331343572-af894dd1-a196-47e8-826a-b801f46e4c66](https://github.com/Udaychaitanya011/VLSI-LAB-EXP-2/assets/161430397/e0ea6b5a-d060-4e01-998d-e53938f6de93)


RESULT

Thus the simulation and synthesis of ENCODER, DECODER, MULTIPLEXER, DEMULTIPLEXER, 2bit MAGNITUDE COMPARATOR using vivado is successfully completed and executed.



