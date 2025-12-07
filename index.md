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
Outline the structure and design of the Verilog code templates you were given. What do they do? Include reference to how a VGA interface works. Guideline: 2/3 short paragraphs, consider including screenshot(s).
### **Simulation**
Explain the simulation process. Reference any important details, include a well-selected screenshot of the simulation. Guideline: 1/2 short paragraphs. 




   
### **Synthesis**
Describe the synthesis and implementation processes. Consider including 1/2 useful screenshot(s). Guideline: 1/2 short paragraphs.
### **Demonstration**
<img src="https://raw.githubusercontent.com/ssjgud12/fpga-vga-verilog/main/docs/assets/images/Screenshot 2025-12-07 125941.png



## **My VGA Design Edit**
In ColourStripes the example code given to us it seperated 8 colours into 8 equal lines spreading across the monitor, with each colour taking up about 80 pixels so i thought if i could change the colour to whatever one i want and increase the amount of pixels used for each coloured i would be able to draw a flag.



### **Code Adaptation**
Briefly show how you changed the template code to display a different image. Demonstrate your understanding. Guideline: 1-2 short paragraphs.

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


### **Synthesis**
Describe the synthesis & implementation outputs for your design, are there any differences to that of the original design? Guideline 1-2 short paragraphs.


### **Demonstration**
If you get your own design working on the Basys3 board, take a picture! Guideline: 1-2 sentences.

<img src="https://raw.githubusercontent.com/ssjgud12/fpga-vga-verilog/main/docs/assets/images/Screenshot 2025-12-07 125903.png">
<img src="https://raw.githubusercontent.com/ssjgud12/fpga-vga-verilog/main/docs/assets/images/Screenshot 2025-12-07 125918.png">
<img src="https://raw.githubusercontent.com/ssjgud12/fpga-vga-verilog/main/docs/assets/images/Screenshot 2025-12-07 125925.png">


## **More Markdown Basics**
This is a paragraph. Add an empty line to start a new paragraph.

Font can be emphasised as *Italic* or **Bold**.

Code can be highlighted by using `backticks`.

Hyperlinks look like this: [GitHub Help](https://help.github.com/).

A bullet list can be rendered as follows:
- vectors
- algorithms
- iterators

Images can be added by uploading them to the repository in a /docs/assets/images folder, and then rendering using HTML via githubusercontent.com as shown in the example below.

<img src="https://raw.githubusercontent.com/melgineer/fpga-vga-verilog/main/docs/assets/images/VGAPrjSrcs.png">
