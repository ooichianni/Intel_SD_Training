## Table of contents
* [ Day_0 : System/Tool Setup Check & GitHub ID creation ](https://github.com/ChianNi/Intel_SD_Training/blob/main/Readme_sd_training.md#day_0--systemtool-setup-check--github-id-creation)
* [ Day_1 : Introduction to Verilog RTL design and Synthesis ](https://github.com/ChianNi/Intel_SD_Training/blob/main/Readme_sd_training.md#day_1--introduction-to-verilog-rtl-design-and-synthesis)

#
# Day_0 : System/Tool Setup Check & GitHub ID creation


### *__Lecture Session__*

**(A) Introduction on Package**

1. IC packaging refers to the material that contains a semiconductor device
2. The wafer level chip scale package (WLCSP) is a variant of the flip-chip interconnection technique where all packaging is done at the wafer level. With WLCSPs, the active side of the die is inverted and connected to the printed circuit board (PCB) using solder balls  
<img width="301" alt="packagetype" src="https://user-images.githubusercontent.com/118953915/203907496-1f4e1038-a868-402e-9e2d-ecaf64505b54.PNG" width=20& height=20%>
 (i) QFN (Quad flat no-lead package) is a leadless package that comes in small size and offers moderate heat dissipation in PCBs <-popular

 (ii) QFP{Quad flat package) is a surface-mounted integrated circuit package with "gull wing" leads extending from each of the four sides.  
<img width="301" alt="package3" src="https://user-images.githubusercontent.com/118953915/203914693-f3ca5866-f174-429c-8297-9e432c957e43.PNG">  

3. Details on architecture:   
(i) Wire board- Connect chip (Wire bonding is the process of creating electrical interconnections between semiconductors (or other integrated circuits) and silicon chips)    
(ii) I/O Pads-Intermediate structures connecting internal signals from the core of the integrated circuit to the external pins of the chip package  
(iii) Core-All fundamental logic of the design (eg: AND gates,pnoms,...) is placed  
(iv) Die-Consists of core, is small semiconductor material specimen on which the fundamental circuit is fabricated  
(v) IP core (intellectual property core)-functional block of logic or data used to make a field-programmable gate array (FPGA) or application-specific integrated circuit for a product (Eg of Foundry IPis: PLL (phase lock loop), SRAM,..)  
(vi) Macros-IP which is available in google that can directly use in own design (eg:memories, CBB(custom building block))


**(B) Concept on communication Software & Hardware**
1. Synthesis is process of transferring higher level of abstraction (RTL) to implementable lower level of abstraction.  
--> It is the process of transforming RTL to gate-level netlist  
2. Compiler will translate a high level programming language's source code (Java/C++) into machine level language code  
3. Assembler is a program that takes basic computer instructions and converts them into a pattern of bits that the computer's processor can use to perform its basic operations (in binary form)

Here is the Overview that show by instructor:  
![Concept](https://user-images.githubusercontent.com/118953915/203926658-55d68a6b-4f1e-4df3-9111-595c4a44e531.png)


#
### *__Lab Session__*

Setup directory and invoke icc2

>Lab steps: [DAY_0..txt](https://github.com/ChianNi/Intel_SD_Training/files/10088800/DAY_0.txt)

Here is the screenshot of lab final outputs:

![day_0](https://user-images.githubusercontent.com/118953915/203699203-8f3cccc3-8cdc-4494-a25d-3d6e29c3d7ba.JPG)


#
# Day_1 : Introduction to Verilog RTL design and Synthesis


### *__Lecture Session__*

**(A) Introduction to open-source simulator iverilog**
>Course Website -> https://vsdiat.com/course_content?uniqueid=20220801054525  
1. Simulator --> Will using iverilog for this training onwards  
Tool for checking RTL design (implementation of spec) by simulating the design (looks for changes on the input signals and output is evaluated. If no changes in input then output also will not have any changes)  
- Design: Verilog codes which has the intended functionality to meet with the required specifications  
- TestBench (TB): setup to apply stimulus (test_vectirs) to the design to checks its functionality by observe the outputs whether obeys to the spec of the design  
Design+Test Bench --> iverilog --> vcd file (value chnage dump format-looking for changes in value) -> gtkwave (this use to view output)

#
### *__Lab Session__*
Lab1: Introduction to lab  
Command to install workshop-> git clone https://github.com/kunalg123/sky130RTLDesignAndSynthesisWorkshop.git  
<img width="639" alt="lab1" src="https://user-images.githubusercontent.com/118953915/205265411-2feb1121-9cdd-44d7-9120-36c80d5741d9.PNG">
In the directory consists:
my_lib: contain library files (lib-contain std cell for synthesis in .lib and verlog_model-contain std cell verilog model in .v)
verilog_files: contain verilog source file and testbench file

Lab2: Introduction iverilog gtkwave part 1
Command: 
(i) Load mux to stimulator-> iverilog good_mux.v tb_good_mux.v , then new file created: a.out
(ii) Execute this new created file from (i)-> ./a.out, then will dump out tb_good_mux.vcd
(iii) Launch waveform-> gtkwave tb_good_mux.vcd
(iv) Click the design and drag the signals into the window and click "Zoom Fit" on the toolbar 
)
