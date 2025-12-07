---
Layout: home
Title: FPGA VGA Driver Project
Tags: fpga vga verilog
Categories: demo
---
Hello my name is Alvin Olayemi im a third year software and electronic student and this is my soc 
(System on Chip Verification) project for my soc module.

## **Template VGA Design**
### **Project Set-Up**
In Vivado I added Testbench,ColourStripes,Bassy3_Master.xdc file to my project, these files were given by our Lecturer to Serve as a starting point in the project. The first step was fixing the code in Testbench which still used the previous example code (ColourCycle), update that adding a 25Mhz clock signal run synthesis and implementation.

<img src="https://raw.githubusercontent.com/ssjgud12/fpga-vga-verilog/main/docs/assets/images/Screenshot%202025-12-02%20143608.png">



### **Template Code**

I was given two template Verilog code ColourStripes and ColourCycle, I have a screenshot of what ColourStripes outputs from the board but i forgot to get one for colourcycle,Colourstripes creates 8 colours 8 rows of colours that take up the whole monitor by expanding and changing the colours used in stripes I was able to create the flag of my choice.

The VGA interface operates by generating precise sync pulses along with rgb colour signals, the pixels are scanned from left to right and from top to bottom asserting hsync at the end of each line and vsync at the end of each frame

### **Demonstration**
<img src="https://raw.githubusercontent.com/ssjgud12/fpga-vga-verilog/main/docs/assets/images/Screenshot 2025-12-07 125941.png">



## **My VGA Design Edit**
In ColourStripes the example code given to us it seperated 8 colours into 8 equal lines spreading across the monitor, with each colour taking up about 80 pixels so i thought if i could change the colour to whatever one i want and increase the amount of pixels used for each coloured i would be able to draw a flag.



### **Code Adaptation**


To change the template code to display a different image first i messed around with the size and colour, the amount of space being taken up by a colour was determined by this line of code

 if(col >= 11'd0 && col <11'd320) begin //black
      red_next   <= 4'b0000;
      green_next <= 4'b0000;
      blue_next  <= 4'b0000;
   end
what this specific piece of code does it takes up the whole left hand side of the monitor, 320 pixels and the rgb values all set to zero gives the colour black,

 else if(col >= 11'd320 && col < 11'd640) begin  //yellow
     red_next   <= 4'b1111;
      green_next <= 4'b1111;
      blue_next  <= 4'b0000;
   end

And with the other line i wanted it to take up the rest of the space on the monitor and change it to another colour to act as like a dummy flag to check if it would be possible to create flags with manipulating the pixel sizing and rgb values.


<img src="https://raw.githubusercontent.com/ssjgud12/fpga-vga-verilog/main/docs/assets/images/Screenshot 2025-12-07 125933.png">




### **Simulation**
Show how you simulated your own design. Are there any things to note? Demonstrate your understanding. Add a screenshot. Guideline: 1-2 short paragraphs.

The simulation is run by execuiting a testbench that drives clk,rst then looking at signals,in simulation the horizontal and vertical sync (hsync,vsync) remain stable while row[10:0],col[10:0] The signals also show vid_on active during the high display region and rgb outputs changing only when the current pixel is inside the visible area.


<img src="https://raw.githubusercontent.com/ssjgud12/fpga-vga-verilog/main/docs/assets/images/Screenshot 2025-12-02 143329.png">




### **Demonstration**
<img src="https://raw.githubusercontent.com/ssjgud12/fpga-vga-verilog/main/docs/assets/images/Screenshot 2025-12-07 125903.png">
<img src="https://raw.githubusercontent.com/ssjgud12/fpga-vga-verilog/main/docs/assets/images/Screenshot 2025-12-07 125918.png">
<img src="https://raw.githubusercontent.com/ssjgud12/fpga-vga-verilog/main/docs/assets/images/Screenshot 2025-12-07 125925.png">




<img src="https://raw.githubusercontent.com/melgineer/fpga-vga-verilog/main/docs/assets/images/VGAPrjSrcs.png">
