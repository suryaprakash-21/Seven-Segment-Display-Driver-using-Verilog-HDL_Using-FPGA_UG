
# Seven-Segment-Display-Driver-using-Verilog-HDL_Using-FPGA
# EXP NO: 2.B Seven-Segment Display Implementation in Spartan-7 FPGA
# Aim
To design and simulate a Verilog HDL seven-segment display driver that converts a 4-bit binary input into the corresponding digits 0–9.

# Apparatus Required
Vivado 2023.1
Spartan 7 FPGA

# Procedure
1. Launch Vivado 2023.1
Open Vivado 2023.1 and create a new project.
Select RTL Project and enable Do not specify sources at this time.
2. Create Verilog Design File
Create a new Verilog design file.
Type the Verilog code for the Seven Segment Display.
The code should convert a 4-bit input into the corresponding seven-segment output.
3. Create Constraint File
Create a new XDC constraint file.
Assign the FPGA pins for input switches, output segments, and the common anode/cathode according to the Real Digital Boolean Board (XC7S50CSGA324-1) pin mapping.
4. Synthesize the Design
Click on Run Synthesis to check for design correctness.
Ensure there are no syntax or mapping errors.
5. Implement the Design
After successful synthesis, click on Run Implementation.
Verify timing and pin placement in the implementation summary.
6. Generate Bitstream
Click Generate Bitstream to create the programming file.
Wait for the process to complete.
7. Program the FPGA
Connect the Boolean Board to your PC.
Open Hardware Manager, click Open Target → Auto Connect, and program the device with the generated bitstream.
8. Observe the Output
Use the 4-bit DIP switches to provide binary inputs.
Observe the Seven Segment Display showing the corresponding digits 0–9.

# Verilog Code for Seven-Segment Display
```
module bcd_to_7_seg_fpga(bcd,seg,an);
    input [3:0] bcd;
    output reg [6:0] seg;
    output reg [3:0] an;
    
    always @ (*)
    begin
        an<=4'b1110;
        case(bcd)
            4'b0000: seg = 7'b1000000;
            4'b0001: seg = 7'b1111001;
            4'b0010: seg = 7'b0100100;
            4'b0011: seg = 7'b0110000;
            4'b0100: seg = 7'b0011001;
            4'b0101: seg = 7'b0010010;
            4'b0110: seg = 7'b0000010;
            4'b0111: seg = 7'b1111000;
            4'b1000: seg = 7'b0000000;
            4'b1001: seg = 7'b0010000;
            4'b1010: seg = 7'b0001000;
            4'b1011: seg = 7'b0000011;
            4'b1100: seg = 7'b1000110;
            4'b1101: seg = 7'b0100001;
            4'b1110: seg = 7'b0000110;
            4'b1111: seg = 7'b0001110;
            default: seg = 7'b1111111;
        endcase
    end
endmodule

```

# Constraint file for Seven-Segment Display
```
## DIP SWITCHES
set_property -dict { PACKAGE_PIN V2 IOSTANDARD LVCMOS33 } [get_ports {bcd[0]}]
set_property -dict { PACKAGE_PIN U2 IOSTANDARD LVCMOS33 } [get_ports {bcd[1]}]
set_property -dict { PACKAGE_PIN U1 IOSTANDARD LVCMOS33 } [get_ports {bcd[2]}]
set_property -dict { PACKAGE_PIN T2 IOSTANDARD LVCMOS33 } [get_ports {bcd[3]}]

## 7-SEGMENT DISPLAY
set_property -dict { PACKAGE_PIN D7 IOSTANDARD LVCMOS33 } [get_ports {seg[0]}]
set_property -dict { PACKAGE_PIN C5 IOSTANDARD LVCMOS33 } [get_ports {seg[1]}]
set_property -dict { PACKAGE_PIN A5 IOSTANDARD LVCMOS33 } [get_ports {seg[2]}]
set_property -dict { PACKAGE_PIN B7 IOSTANDARD LVCMOS33 } [get_ports {seg[3]}]
set_property -dict { PACKAGE_PIN A7 IOSTANDARD LVCMOS33 } [get_ports {seg[4]}]
set_property -dict { PACKAGE_PIN D6 IOSTANDARD LVCMOS33 } [get_ports {seg[5]}]
set_property -dict { PACKAGE_PIN B5 IOSTANDARD LVCMOS33 } [get_ports {seg[6]}]
set_property -dict { PACKAGE_PIN A6 IOSTANDARD LVCMOS33 } [get_ports {seg[7]}]

## ANODE CONTROL
set_property -dict { PACKAGE_PIN D5 IOSTANDARD LVCMOS33 } [get_ports {an[0]}]
set_property -dict { PACKAGE_PIN C4 IOSTANDARD LVCMOS33 } [get_ports {an[1]}]
set_property -dict { PACKAGE_PIN C7 IOSTANDARD LVCMOS33 } [get_ports {an[2]}]
set_property -dict { PACKAGE_PIN A8 IOSTANDARD LVCMOS33 } [get_ports {an[3]}]
```

# FPGA Implementation Output

![7segment display](https://github.com/user-attachments/assets/ab6f47d0-6476-4598-903c-38449c1b40f8)

# Conclusion
In this experiment, a seven-segment display driver was successfully implemented using Verilog HDL in FPGA.This experiment demonstrates the practical application of Verilog HDL in designing and controlling digital hardware components, highlighting its importance in developing reliable and efficient digital systems.
