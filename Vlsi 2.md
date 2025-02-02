# Vlsi-2
module ALU (A,B,aluout,carryout,alusel);

input [7:0]A,B;

input [3:0]alusel;

output[7:0]aluout;

output carryout;

reg [7:0]aluresult;

wire [8:0]temp;

assign aluout=aluresult;

assign temp={4'b0000}+{4'b0000};

assign carryout=temp[8];

always@(*)

begin

case(alusel)

4'b0000:

aluresult=(A+B);

4'b0001:

aluresult=(A-B);

4'b0010:

aluresult=(A*B);

4'b0011:

aluresult=(A/B);

4'b0100:

aluresult=(A<<1);

4'b0101:

aluresult=(A>>1);

4'b0110:

aluresult={A[6:0],A[7]};

4'b0111:

aluresult={A[0],A[7:1]};

4'b1000:

aluresult=(A&B);

4'b1001:

aluresult=(A|B);

4'b1010:

aluresult=(A^B);

4'b1011:

aluresult=(~(A&B));

4'b1100:

aluresult=(~(A|B));

4'b1101:

aluresult=(~(A^B));

4'b1110:

aluresult=(A>B)?8'd1:8'd0;

4'b1111:

aluresult=(A==B)?8'd1:8'd0;

default:

aluresult=A+B;

endcase

end

endmodule

