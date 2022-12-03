## Table of contents
* [ Day_0 : System/Tool Setup Check & GitHub ID creation ](https://github.com/ChianNi/Intel_SD_Training/blob/main/Readme_sd_training.md#day_0)
* [ Day_1 : Introduction to Verilog RTL design and Synthesis ](https://github.com/ChianNi/Intel_SD_Training/blob/main/Readme_sd_training.md#day_1--introduction-to-verilog-rtl-design-and-synthesis)

#
# Day_0 
**⭐System/Tool Setup Check & GitHub ID creation**


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
# Day_1   
**⭐Introduction to Verilog RTL design and Synthesis**


### *__Lecture Session__*

**(A) Introduction to open-source simulator iverilog**
>Course Website -> https://vsdiat.com/course_content?uniqueid=20220801054525  
1. Simulator --> Will use iverilog for this training onwards  
Tool for checking RTL design (implementation of spec) by simulating the design (looks for changes on the input signals and output is evaluated. If no changes in input then output also will not have any changes)  
-Design: Verilog codes which has the intended functionality to meet with the required specifications  
-TestBench (TB): setup to apply stimulus (test_vectirs) to the design to checks its functionality by observe the outputs whether obeys to the spec of the design  
Design+Test Bench --> iverilog --> vcd file (value chnage dump format-looking for changes in value) -> gtkwave (this use to view output)

#
### *__Lab Session__*
*Lab1: Introduction to lab*  
Command to install workshop-> git clone https://github.com/kunalg123/sky130RTLDesignAndSynthesisWorkshop.git  
<img width="600" alt="lab1" src="https://user-images.githubusercontent.com/118953915/205265411-2feb1121-9cdd-44d7-9120-36c80d5741d9.PNG">  
In the directory consists:
my_lib: contain library files (lib-contain std cell for synthesis in .lib and verlog_model-contain std cell verilog model in .v)
verilog_files: contain verilog source file and testbench file

*Lab2: Introduction iverilog gtkwave part 1*  
Steps:     
(i) Load mux to stimulator-> iverilog good_mux.v tb_good_mux.v , then new file created: a.out    
(ii) Execute this new created file from (i)-> ./a.out, then will dump out tb_good_mux.vcd     
<img width="600" alt="lab1l" src="https://user-images.githubusercontent.com/118953915/205426153-fbd574f1-4bf7-4175-b545-fb752fcaa235.png">  
(iii) Click the design and drag the signals into the window and click "Zoom Fit" on the toolbar     
<img width="600" alt="lab1b" src="https://user-images.githubusercontent.com/118953915/205270195-f6e6eb96-0ca4-413d-90a4-fd6cf33dd718.PNG">  
From the waveform: When the sel is "1", the output(y) will follow the input(i1)

*Lab2: Introduction iverilog gtkwave part 2*  
Understanding the content:  
vi tb_good_mux.v & vi good_mux.v (suppose is this command->gvim tb_good_mux.v -o good_mux.v)
![lab1e](https://user-images.githubusercontent.com/118953915/205290366-3d96a298-204f-4172-a602-1502fe829a66.png)  
testbench no primary input and output, but got design instantiate- UUT (Unit under test) or DUT (Design under test)

### *__Lecture Session__*

**(B) Introduction to Yosys and Logic synthesis**
1. Synthesizer --> Will use Yosys for this training onwards  
Tool used for converting the RTL to netlist (in the form of std cell)
2. Design + .lib --> yosys --> netlist file  
Use read_verilog to read the Design ; Use read_liberty to read .lib ; write_verilog to write the netlist file  
3. Verify the synthesis  
Design+Test Bench --> iverilog --> vcd file -> gtkwave  
--> must ensure same as output observed during RTL simulation
4. The set of primary inputs/outputs will remain the same between the RTL design and synthesize netlist -> same test bench can be used  
5. RTL design: Behavioral representation of the required specification  
RTL Code (Verilog HDL) --> Digital logic circuit (hardware circuit)  
6. RTL to gate level translation - design converted into gates and the connections are made between the gates, output file: netlist  
7. Collection of logical modules in formal .lib  
-basic logix gates: AND,OR,...  
-different floavors of same gate: 2 input AND gate, 3 input AND gate, slow/medium/fast...
8. Combinational delay in logic path determines the max speed of operation of digital logic circuit  
(i) Fast cell needed to meet setup:
Tclk> TF1+Tcombi+TsetupofF2 (data must be stable before the capturing edge of clock)  
fclkmax=1/Tclkmin (low period==high freq==fast speed==max performance, so means delay must less, must faster cell, Tcombi must less)    
(i) Slow cell needed to meet hold
TholdF2<TF1+Tcombi  
so the .lib will have various collection of logical modules with difference behaviour  
9. Load in digital logic circuit is capacitance  
-Faster the charging/discharging of capacitance, lesser the propagation delay  
 -so need transistors capable of sourcing more current (wider transistors==low delay==more area&power<- not good)  
10. Need to guide the syn thesizer to select the flavour of cells that is optimum fo rthe implementation of logic circuit  
fast cell-> comsume high power and area, causing hold violation  
slow cell-> not meet performance  
So constraints is needed as a guidance for the 
   
#
### *__Lab Session__*
*Lab3: good mux Part 1,2,3*  

Steps:  
Command to invoke yoysy > yosys  
(i) Read library-> read_liberty -lib ../my_lib/lib/sky*.lib  
(ii) Read design-> read_verilog good_mux.v  
(iii) Synthesis-> synth -top good_mux  
(iv) thn can generate netlist -> abc -liberty ../lib/sky*.lib (std cell will get pick from library)    
<img width="600" alt="lab1g" src="https://user-images.githubusercontent.com/118953915/205316337-5ccd9b3d-7cef-4cf6-81a4-b8e5953c8b86.png">  
(v) See logic realiazed in graphicel -> show        
There is 3 input, 1 output, no internal wire, 1 mux 2to1    
<img width="600" alt="lab1h" src="https://user-images.githubusercontent.com/118953915/205317486-e3c559a1-19c9-484a-84b4-29cb7ceeeaf6.png">  
-nand2_1: nand gate with 2 input, o2ai: OR+AND+INV  
(vi) Write netlist-> write_verilog  good_mux_netlist.v / write_verilog -noattr good_mux_netlist.v <- simplified netlist    
<img width="600" alt="lab1j" src="https://user-images.githubusercontent.com/118953915/205425197-8e128ef0-7944-4afc-b11d-f8531c5ccdd2.png">  

Here is my nelist and logic diagram:  
<img width="600" alt="lab1k" src="https://user-images.githubusercontent.com/118953915/205425631-f8eab904-fe59-4ae1-9bc7-97f259758fc6.png">


