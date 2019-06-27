# spectre

`timescale 1ns / 1ps

module modified( clk_in);//tag, index, 
 reg[15:0]T;
 //reg [11:0]T[15:4];
 reg [4:0]location;
 reg[6:0]out_cache;
 reg y;
 reg [27:1]z;
 reg[3:0] temp;
 reg[11:0] intermediate;
 reg cache_hit;
 reg[11:0]tag[15:0];
 reg[6:0]data[15:0];
  input clk_in;
  wire clk, clk_100M;
 wire[4:0]X;
 reg[3:0]index;
 reg[4:0]w;
 reg[4:0] store[25:0];
 reg[15:0] A[26:1];
 reg [6:0] main[26:1];
 parameter size=15;
 integer i=1;
 initial begin
   store[0]=5'b00001;
	store[1]=5'b00010;
   store[2]=5'b00011;
	store[3]=5'b00100;
	store[4]=5'b00101;
   store[5]=5'b00110;
	store[6]=5'b00111;
	store[7]=5'b01000;
	store[8]=5'b01001;
	store[9]=5'b01010;
   store[10]=5'b01011;
   store[11]=5'b01100;		 
   store[12]=5'b01101;
   store[13]=5'b01110;
	store[14]=5'b01111;
	store[15]=5'b10000;
   store[16]=5'b10001;
	store[17]=5'b10010;
	store[18]=5'b10011;
	store[19]=5'b10100;
	store[20]=5'b10101;
	store[21]=5'b10110;
	store[22]=5'b10111;
	store[23]=5'b11000;
	store[24]=5'b11001;
	store[25]=5'b11010;
end
initial begin
		// Initialize Inputs
	//VICTIM MEMORY	
    A[1]=16'b1000000000000001;
	A[2]=16'b1100000000000010;
    A[3]=16'b1110000000000011;
    A[4]=16'b1111000000000100;
    A[5]=16'b1111100000000101;
    A[6]=16'b1111110000000110;
    A[7]=16'b1111000000000111;
    A[8]=16'b1111100000001000;
    A[9]=16'b1111111111111001;
    A[10]=16'b1111111000001010;
    A[11]=16'b1111111000001011;
    A[12]=16'b1111111100001100;
	A[13]=16'b1111111110001101;
	A[14]=16'b1111111111001110;
	A[15]=16'b1111111111101111;
	A[16]=16'b0000000000110000;
	A[17]=16'b0000000001110001;
    A[18]=16'b0000000011110010;
	A[19]=16'b000000111110011;
	A[20]=16'b1000001111110100;
    A[21]=16'b0000001111110101;
	A[22]=16'b0000011111110110;
	A[23]=16'b0000111111110111;
	A[24]=16'b0001111111111000;
	A[25]=16'b0011111111111001;
	A[26]=16'b0111111111111010;
	end
	initial begin 
	//FORBIDDEN DATA
	main[1]=7'b1100001;//a
	main[2]=7'b1100010;//b
	main[3]=7'b1100011;//c
	main[4]=7'b1100100;//d
	main[5]=7'b1100101;//e
	main[6]=7'b1100110;//f
	main[7]=7'b1100111;//g
	main[8]=7'b1101000;//h
	main[9]=7'b1101001;//i
	main[10]=7'b1101010;//j
	main[11]=7'b1101011;//k
	main[12]=7'b1101100;//l
	main[13]=7'b1101101;//m
	main[14]=7'b1101110;//n
	main[15]=7'b1101111;//o
	main[16]=7'b1110000;//p
	main[17]=7'b1110001;//q
	main[18]=7'b1110010;//r
	main[19]=7'b1110011;//s
	main[20]=7'b1110100;//t
	main[21]=7'b1110101;//u
	main[22]=7'b1110110;//v
	main[23]=7'b1110111;//w
	main[24]=7'b1111000;//x
	main[25]=7'b1111001;//y
	main[26]=7'b1111010;//z
	end
always @(posedge clk)
begin
     
	  w=store[{X[4],X[3],X[2],X[1],X[0]}]; 
  T=A[{w[4],w[3],w[2],w[1],w[0]}];
		   if(X<size)
	 y=1'b1;//input is correct
	  else 
	   y=1'b0;//input is malicious
end
 always @(posedge clk)
 begin
  index=T[3:0];
  T[15:4]=T[15:4];
end	 
always @(posedge clk)
begin
  case(index)
4'b0000:

begin
	tag[0]=T[15:4];
	data[0]=main[{T[4],T[3],T[2],T[1],T[0]}];
end
4'b0001:
begin
	tag[1]=T[15:4];
	data[1]=main[{T[4],T[3],T[2],T[1],T[0]}];
end
4'b0010:
begin
	tag[2]=T[15:4];
	data[2]=main[{T[4],T[3],T[2],T[1],T[0]}];
end
4'b0011:
begin
	tag[3]=T[15:4];
	data[3]=main[{T[4],T[3],T[2],T[1],T[0]}];
end
4'b0100:
begin

	tag[4]=T[15:4];
	data[4]=main[{T[4],T[3],T[2],T[1],T[0]}];
end
4'b0101:
begin
	tag[5]=T[15:4];
	data[5]=main[{T[4],T[3],T[2],T[1],T[0]}];
end
4'b0110:
begin
	tag[6]=T[15:4];
	data[6]=main[{T[4],T[3],T[2],T[1],T[0]}];
end
4'b0111:
begin
	tag[7]=T[15:4];
	data[7]=main[{T[4],T[3],T[2],T[1],T[0]}];
end
4'b1000:
begin
	tag[8]=T[15:4];
	data[8]=main[{T[4],T[3],T[2],T[1],T[0]}];
end
4'b1001:
begin
	tag[9]=T[15:4];
	data[9]=main[{T[4],T[3],T[2],T[1],T[0]}];
end
4'b1010:
begin
	tag[10]=T[15:4];
	data[10]=main[{T[4],T[3],T[2],T[1],T[0]}];
end
4'b1011:
begin
	tag[11]=T[15:4];
	data[11]=main[{T[4],T[3],T[2],T[1],T[0]}];
	tag[10]=12'b0;
end
4'b1100:
begin
	tag[12]=T[15:4];
	data[12]=main[{T[4],T[3],T[2],T[1],T[0]}];
end
4'b1101:
begin
	tag[13]=T[15:4];
	data[13]=main[{T[4],T[3],T[2],T[1],T[0]}];
end
4'b1110:
begin
	tag[14]=T[15:4];
	data[14]=main[{T[4],T[3],T[2],T[1],T[0]}];
end
4'b1111:
begin
	tag[15]=T[15:4];
	data[15]=main[{T[4],T[3],T[2],T[1],T[0]}];
end
  endcase
 end

 initial begin 
	z=27'b0;
 end

always @(posedge clk)
 begin
if(i>=1 && i<27)
begin
	temp=A[i][3:0];
	intermediate=A[i][15:4];
if(tag[temp]==intermediate)
	begin 
	cache_hit=1'b1;
	location=store[i-1];
	z[i-1]<=1'b1;
	out_cache=main[i];
	error(i-1);
	i<=i+1;
	end
else 
	begin
	z[i-1]<=1'b0;
	cache_hit=1'b0;
	i<=i+1;
	end 
end
else if(i>=27)
	begin
	cache_hit=1'b0;
	i<=1'b1;
	z<=27'b00000000000000000000000000;

//	//flushing the data
//	tag[0]<=12'b0;
//	tag[1]<=12'b0;
//	tag[2]<=12'b0;
//	tag[3]<=12'b0;
//	tag[4]<=12'b0;
//	tag[5]<=12'b0;
//	tag[6]<=12'b0;
//	tag[7]<=12'b0;
//	tag[8]<=12'b0;
//	tag[9]<=12'b0;
//	tag[10]<=12'b0;
//	tag[11]<=12'b0;
//	tag[12]<=12'b0;
//	tag[13]<=12'b0;
//	tag[14]<=12'b0;
//	tag[15]<=12'b0;
    
    data[0]<=7'b0;
    data[1]<=7'b0;
    data[2]<=7'b0;
    data[3]<=7'b0;
    data[4]<=7'b0;
    data[5]<=7'b0;
    data[6]<=7'b0;
    data[7]<=7'b0;
    data[8]<=7'b0;
    data[9]<=7'b0;
    data[10]<=7'b0;
    data[11]<=7'b0;
    data[12]<=7'b0;
    data[13]<=7'b0;
    data[14]<=7'b0;
    data[15]<=7'b0;
    end
end
 
 
 task error;
	  input integer s; 
 $display("Hit at location:%d",s);
 endtask
 
 vio_0 modified_vio (
   .clk(clk_100M),                // input wire clk
   .probe_in0(T),    // input wire [15 : 0] probe_in0
   .probe_in1(y),    // input wire [0 : 0] probe_in1
   .probe_in2(w),    // input wire [4 : 0] probe_in2
   .probe_in3(z),    // input wire [26 : 0] probe_in3
   .probe_in4(index),    // input wire [3 : 0] probe_in4
   .probe_in5(temp),    // input wire [3 : 0] probe_in5
   .probe_in6(intermediate),    // input wire [11 : 0] probe_in6
   .probe_in7(cache_hit),    // input wire [0 : 0] probe_in7
   .probe_in8(out_cache),    // input wire [6 : 0] probe_in8
   .probe_in9(location),    // input wire [4 : 0] probe_in9
   .probe_out0(X)  // output wire [4 : 0] probe_out0
 );
  
 
 ila_0 modified_ila (
     .clk(clk_100M), // input wire clk
 
 
     .probe0(clk), // input wire [0:0]  probe0  
     .probe1(X), // input wire [4:0]  probe1 
     .probe2(T), // input wire [15:0]  probe2 
     .probe3(y), // input wire [0:0]  probe3 
     .probe4(w), // input wire [4:0]  probe4 
     .probe5(z), // input wire [26:0]  probe5 
     .probe6(index), // input wire [3:0]  probe6 
     .probe7(temp), // input wire [3:0]  probe7 
     .probe8(intermediate), // input wire [11:0]  probe8 
     .probe9(cache_hit), // input wire [0:0]  probe9 
     .probe10(out_cache), // input wire [6:0]  probe10 
     .probe11(location) // input wire [4:0]  probe11
 );
 
  clk_wiz_0 clocling_wiz
   (
    // Clock out ports
    .clk_out1(clk_100M),     // output clk_out1
    .clk_out2(clk),     // output clk_out2
   // Clock in ports
    .clk_in1(clk_in)); 
 
endmodule
