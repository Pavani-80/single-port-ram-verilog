design.sv
module single_port_ram (
    input wire clk,
    input wire we,
    input wire [3:0] addr,
    input wire [7:0] din,
    output reg [7:0] dout
);
    // 16 x 8-bit memory
    reg [7:0] mem [15:0];

    always @(posedge clk) begin
        if (we)
            mem[addr] <= din;      // Write operation
        else
            dout <= mem[addr];     // Read operation
    end
endmodule

testbench.sv
module testbench;
  reg clk;
  reg we;
  reg [3:0] addr;
  reg [7:0] din;
  wire [7:0] dout;

  // Instantiate the RAM
  single_port_ram uut (.clk(clk), .we(we), .addr(addr), .din(din), .dout(dout));

  // Clock generation
  always #5 clk = ~clk;

  initial begin
    $dumpfile("waveform.vcd");
    $dumpvars(0, testbench);

    $display("Start Simulation");
    clk = 0;
    we = 0;
    addr = 0;
    din = 0;

    // Write operation
    #10 we = 1; addr = 4'h1; din = 8'hA5;
    #10 addr = 4'h2; din = 8'h3C;
    #10 addr = 4'h3; din = 8'h7E;

    // Read operation
    #10 we = 0;
    #10 addr = 4'h1;
    #10 $display("Read from addr 1: %h", dout);
    #10 addr = 4'h2;
    #10 $display("Read from addr 2: %h", dout);
    #10 addr = 4'h3;
    #10 $display("Read from addr 3: %h", dout);

    #10 $finish;
  end
endmodule

![output compilation](https://github.com/user-attachments/assets/c69f0b4b-eb03-4ab4-85ce-7b834452dc60)

![waveform](https://github.com/user-attachments/assets/8be78eb9-e0a1-424e-a16d-ccd8ffc5beb2)







