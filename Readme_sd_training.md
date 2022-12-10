## Table of contents

+ **[ Day_0 : System/Tool Setup Check & GitHub ID creation ](https://github.com/ChianNi/Intel_SD_Training/blob/main/Readme_sd_training.md#day_0)**
  * [Lab1: Introduction to lab](https://github.com/ChianNi/Intel_SD_Training/blob/main/Readme_sd_training.md#lab1-introduction-to-lab)
  * [Lab2: Introduction iverilog gtkwave](https://github.com/ChianNi/Intel_SD_Training/blob/main/Readme_sd_training.md#lab2-introduction-iverilog-gtkwave-part-1)
+ **[ Day_1 : Introduction to Verilog RTL design and Synthesis ](https://github.com/ChianNi/Intel_SD_Training/blob/main/Readme_sd_training.md#day_1)**
  * [Lab3: yosys good mux](https://github.com/ChianNi/Intel_SD_Training/blob/main/Readme_sd_training.md#lab3-good-mux-part-123)
+ **[ Day_2 : Timing libs(QTMs/ETMs), hierarchical vs flat synthesis and efficient flop coding styles ](https://github.com/ChianNi/Intel_SD_Training/blob/main/Readme_sd_training.md#day_2)**  
  * [Lab4: Introduction to dot Lib](https://github.com/ChianNi/Intel_SD_Training/blob/main/Readme_sd_training.md#lab4-introduction-to-dot-lib) 
  * [Lab5: Hierarchical vs Flat Synthesis](https://github.com/ChianNi/Intel_SD_Training/blob/main/Readme_sd_training.md#lab5-hierarchical-vs-flat-synthesis)
+ **[ Day_3 : Combinational and sequenial optimizations ](https://github.com/ChianNi/Intel_SD_Training/blob/main/Readme_sd_training.md#day_3)** 
  * [Lab6: Combinational Logic Optimisations](https://github.com/ChianNi/Intel_SD_Training/blob/main/Readme_sd_training.md#lab6-combinational-logic-optimisations)
  * [Lab7: Sequential Logic Optimisations](https://github.com/ChianNi/Intel_SD_Training/blob/main/Readme_sd_training.md#lab7-sequential-logic-optimisations) 


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
#### *Lab1: Introduction to lab*  
Command to install workshop-> git clone https://github.com/kunalg123/sky130RTLDesignAndSynthesisWorkshop.git  
<img width="600" alt="lab1" src="https://user-images.githubusercontent.com/118953915/205265411-2feb1121-9cdd-44d7-9120-36c80d5741d9.PNG">  
In the directory consists:
my_lib: contain library files (lib-contain std cell for synthesis in .lib and verlog_model-contain std cell verilog model in .v)
verilog_files: contain verilog source file and testbench file

#### *Lab2: Introduction iverilog gtkwave part 1*  
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
#### *Lab3: good mux Part 1,2,3*  

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


#
# Day_2   
**⭐Timing libs(QTMs/ETMs), hierarchical vs flat synthesis and efficient flop coding styles**


### *__Lecture Session__ & __Lab Session__*

1. CMOS (complementary metal-oxide semiconductor) is the semiconductor technology used in most of today's integrated circuits (ICs), also known as chips or microchips 
There are two types of MOSFETs: the NMOS and the PMOS  
MOSFETs-specifying the circuits physically and characterizing them electricity    
2. FF (flip flop) serves as memory element in a digital design  
3. Setup time is the time for the input data signals to remain stable before the clock edge, while hold time is the time for the input data signals to remain stable  after the clock edge

#### **Lab4: Introduction to dot Lib**    

1. Here is the contents of .libs in this training   
<img width="600" alt="Capture" src="https://user-images.githubusercontent.com/118953915/206341918-17e165df-0d95-4605-8fec-b283f48c8481.PNG">  
<img width="600" alt="lab2a" src="https://user-images.githubusercontent.com/118953915/205808293-af4da4c9-ed20-4912-9573-98451b599ad3.PNG">  
Enter ":syn of" to switch off highlighted word in vim

(i)Name of library: sky130_fd_sc_hd_tt_025c_1v80      
(ii)PVT (Process,Voltage,Temperature)  
-Process variation due to fabrication (variations in the manufacturing conditions such as temperature, pressure, and dopant concentrations)    
-Voltage will cause variation in behaviour of the circuit    
-Semiconductor sensitive to temperature    
In the library of sky130_fd_sc_hd_tt_025c_1v80:    
tt-typical process (can be slow/fast/typical) ; 025c-temperature ; 1v80 -volatge    

In order to make sure our silicon can be function in all possible conditions  
we need to factor in all variation when we design circuit, so our library will be charaterize to model this variations  

2. .lib is buckect of all std cell that avaiable  
Containing different flavours of different cell & different flavours of same cell with different number of inputs   
<img width="600" alt="lab2b" src="https://user-images.githubusercontent.com/118953915/205820406-e6b086cf-35ce-406f-bc61-35f58de851bb.PNG">  
and each of them have different features, can open equivalent verilog model to see the details of gates by using command ":vsp ../my_lib/verilog_model/sky130_fd_sc_hd.v" 
File with <file>.pp.v is consisting power port information 
<img width="600" alt="lab2c" src="https://user-images.githubusercontent.com/118953915/205829566-3b17871b-3a2c-4fa4-a6ad-0141246b6c7c.PNG">  
 we can see that there is
The cell is having 5 inputs, so there will be 2^5=32 combinations. In the libs will state out all details for each combinations (Eg: Leakage power)   
3. Inside the lib will also state out cell area, power port  
<img width="300" alt="lab2d" src="https://user-images.githubusercontent.com/118953915/205839427-24e92d8b-0eb7-4ef8-9550-a420ad39d329.PNG">  
Each of the cell pin have its own information: capacitance, transition, power associated to the pin  
<img width="300" alt="lab2e" src="https://user-images.githubusercontent.com/118953915/205839432-e3914736-c691-48d9-af9c-80976b2b849e.PNG">  
 Besides power, the lib also will contains timing information  
<img width="600" alt="lab2f" src="https://user-images.githubusercontent.com/118953915/205839439-f176fd34-4d19-479c-a2f3-c6ed72a9f1b0.PNG">  
3. Here is the comparison on different flavours of same cell with different number of inputs  
 <img width="900" alt="lab2g" src="https://user-images.githubusercontent.com/118953915/205848330-ab153dd2-9ab3-4542-b802-6c6de19f6e45.PNG">  
-Smaller cell: More delay, Less area, Less power  
-Bigger cell: Less delay, More area, More power  
 
💡Conclusion: 
 -Pros of Bigger cell: wider transisteor == faster/small delay  
 -Pros of Smaller cell: small area == small power comsume

 
#### **Lab5: Hierarchical vs Flat Synthesis**    
 
 1. Command to setup the design:
(i) yosys  
(ii) read_liberty -lib ../lib/sky*.lib  
(iii) read_verilog multiple_modules.v  
(iv) synth -top multiple_modules  
 <img width="500" alt="Capture" src="https://user-images.githubusercontent.com/118953915/206349270-59c806c7-a885-4519-8847-88b0f0a19142.PNG">  
 <img width="300" alt="lab2h" src="https://user-images.githubusercontent.com/118953915/206076867-a565dc90-74d4-432c-ad12-c028c85c5a47.PNG">  
(v) linking deisgn to library  
 abc -liberty ../lib/sky*.lib    
(v) show multiple_modules <- key in the top modules name      
Then will display out the hierarchy design -> not showing AND and OR gate, but only showing the u1 and u2, which is the instance of submodule 1 and 2   
 <img width="600" alt="lab2i" src="https://user-images.githubusercontent.com/118953915/205855372-92273978-5913-4f81-a92e-575f0ea3f9ff.PNG">  
(vi) write_verilog -noattr multiple_modules_hier.v then !vim multiple_modules_hier.v  
  > Refer this link for learning DeMorgan's Theorems in boolean algebra:  https://www.allaboutcircuits.com/textbook/digital/chpt-7/demorgans-theorems/    
 
 My run:   
 <img width="600" alt="Capture" src="https://user-images.githubusercontent.com/118953915/206344644-6f9a7367-797e-471c-8f79-4659eb3feb87.PNG">  
 <img width="200" alt="lab2q" src="https://user-images.githubusercontent.com/118953915/206092566-801b13b7-9422-4b92-bada-dc6b26cc4156.PNG">  
 Run from trainning video:   
 <img width="455" alt="lab2j" src="https://user-images.githubusercontent.com/118953915/205927497-d3452277-6b91-4324-8e94-91050a9627cd.PNG">  
(v) Reason on why the netlist construct 2INV+NAND instead of directly OR gate:
Here is the screenshot from lecture video:  
From the figure: [Left] If cmos NAND, have stacked nmos, [Right] NOR follow by iNV to get OR, have staked pmos
<img width="330" alt="lab2k" src="https://user-images.githubusercontent.com/118953915/205933439-d48489b7-8c53-4a1b-8b57-38f57bc2a987.PNG">  
-Stacked pmos is bad, due to poor mobility. In order to improvce this need to make it wide cell (to get good logic effort)

-Logical effort is defined as the ratio of the input capacitance of a gate to the input capacitance of an inverter delivering the same output current. It is defined as the number of times worse it is at delivering output current than would be an inverter with identical input capacitance  
 
(vi) write out flat netlist by using command flatten  
(vii)write_verilog -noattr multiple_modules_flat.v then ! vim multiple_modules_flat.v  
 Here is the comparison among multiple_modules_hier.v vs multiple_modules_flat.v
 <img width="900" alt="lab2l" src="https://user-images.githubusercontent.com/118953915/205939781-4c3ae3d4-cd4c-4123-8d61-db09f5b1b216.PNG">  
From the figure: [Right] it is a single netlist without any submodule inside the flatten.v and can directly see each of the instantiation of the gate  
(viii) Invoke show, not seing u1 and u2 anymore after flattem
 <img width="929" alt="lab2m" src="https://user-images.githubusercontent.com/118953915/205941268-ef256f34-9b8d-4da1-a5b0-39b587688f58.PNG">  
 2. Now looking at sub-modules
 (i) Need to exit and repeat the step from (i) to (iii)   
 (ii) Then, use this command and only synthesis one of the sub_module: synth -top sub_module1 
 <img width="600" alt="Capture" src="https://user-images.githubusercontent.com/118953915/206367130-927887da-4e04-4406-82e9-f350fcc37ba7.PNG">  
 Only consists one sub_module1 which is AND gate:    
 <img width="600" alt="lab2zsub" src="https://user-images.githubusercontent.com/118953915/206192139-d2e9e102-8d68-450a-bde7-bd6e785d4e25.PNG">  

   
💡 Modular synthesis is prefer when we have multiple instances of same module (Eg: when there is 6 x multiplier, only required to synthesize one and duplicate 6 times) or divide and conquer (Eg: when there is huge and massive design, then the tool will not run smartly. Recommend to run by portion so the netlist will get optimize, after that stick all those netlist together at the top level)  
 
 **Various Flop Coding Styles and optimization**  
 
1. In a combinational circuit, there is multiple logic gate. Each of the logic gate will have some propagation delay, which will lead to glitch occur. (Eg: 1st gate having propagtion delay 1ns and the next gate have 2ns, so at the end the output dint have the right value which means that output will glitch due to propagation delay)  
💡 so we need Flop to store the value (place between the gates)  
-Output of the D-FF only will trigger during the positive edge of clocks, so the data at output is stable.  
-The next logic gate will also receive a stable data, because the output(Q) of previous Flop have shielded the changes from its own input(D)
 2. We need to initialize the flops - sel/reset/syn/async   
 <img width="541" alt="Capture" src="https://user-images.githubusercontent.com/118953915/206346230-17b19539-3857-46c4-b9ce-0c032f7b75cc.PNG">  
 <img width="960" alt="lab2p" src="https://user-images.githubusercontent.com/118953915/206098264-9a0301ac-743d-4c7d-ba98-6bcd7fb93914.PNG">
 
 
 All of the output will get trigger as long as there is posedge clock -> "always@(posedge clk)"  
 (i) D FF with async reset: Output(q) will get trigger when there is positive clocck edge and positive async_reset  
-Asynchronous happen anytime irrespective to clock edge (without dependency to clock)    
-When there is positive async_reset, the output will have value "0", else will read in value from input(d)  
(ii) D FF with sync reset: Output(q) will get trigger if condition:   
 -when the sync_reset is toggle to 1, it will wait for posdge of clock, then only will trigger the output    
📖 asyn FF: always (posedge clk,posedge async reset) ; syn FF: always(posedge clk)  
  
**Lab flop syntheses simulation**
1. Here is all the FF, will check the behavioural simulation:  
(i) iverilog dff_*.v tb_dff_*.v  ; ./a.out ; gtkwave <>.vcd    
<img width="1000" alt="lab2r" src="https://user-images.githubusercontent.com/118953915/206105360-d43817af-6876-426b-9ba4-9542abc7ecc0.PNG">  
(ii) Asyn reset  
<img width="600" alt="lab2s" src="https://user-images.githubusercontent.com/118953915/206105370-b1ee39b8-fe08-4b3e-8e1c-72b83cf1113a.PNG">  
 - The output(q) will get trigger for each of the posedge clock    
 - If the async_reset is "1", the output(q) will directly change to "0" irrespective to clock edge  
 - The output(q) will remain "0" until the async_reset is toggle back to "0", then it will read in value from input(d) during posedge clock  

 (iii) Asyn set  
<img width="600" alt="lab2t" src="https://user-images.githubusercontent.com/118953915/206105378-02c19451-6487-495f-8e31-0a11ac56c102.PNG"> 
 - The output(q) will get trigger for each of the posedge clock    
 - If the async_set is "1", the output(q) will directly change to "1" irrespective to clock edge  
 - The output(q) will remain "1" until the async_set is toggle back to "0", then it will read in value from input(d) during posedge clock  

 (iv) Sync reset  
<img width="600" alt="lab2u" src="https://user-images.githubusercontent.com/118953915/206105390-9a0f5015-29fb-45f7-a597-e395247f2500.PNG">  
 - The output(q) will get trigger for each of the posedge clock    
 - If the sync_reset is "1", the output(q) will change to "0" in the next posedge clk  
 - The output(q) will remain "0" until the sync_reset is toggle back to "0", then it will read in value from input(d) during posedge clock  
 
 💡set&reset have higher priority thn input(d) due to if(condition)...else  
 
2. Proceed to synthesis  
(i) Steps: yosys ; read_liberty -lib ../lib/sky*.lib ; read_verilog dff*.v ; synth -top dff_* ; using dff, dfflibmap -liberty ../lib/sky*.lib ; abc -liberty ../lib/sky*.lib  
 <img width="600" alt="Capture" src="https://user-images.githubusercontent.com/118953915/206341471-8c2badc7-f839-4107-abb9-73bf081cdd29.PNG">  
 
-If use dfflimap, then the tool will only search for ff lib (and sometimes all the ff lib will keep in another folder in */lib, so need to point correctly)
only look for dff flops (ss)  
<img width="600" alt="lab2v" src="https://user-images.githubusercontent.com/118953915/206117867-e22b7618-1707-4379-9ebb-68a36c561b47.PNG">  
(ii) async res: stated "RESET", flop is active high reset so need inv (behaviour of AND gate in order to get "1")  
 <img width="600" alt="lab2w" src="https://user-images.githubusercontent.com/118953915/206117885-ebbd4855-52fa-4c31-be0d-696f94c065e1.PNG">    
async set: stated "SET", flop is active high reset so need inv (behaviour of AND gate in order to get "1") 
<img width="600" alt="lab2x" src="https://user-images.githubusercontent.com/118953915/206117889-ee19efe6-7926-4949-ad39-747769d7ea9b.PNG"> 
syncres: no set/reset pin on ff  
 Explanation from training video:
 <img width="800" alt="lab2y" src="https://user-images.githubusercontent.com/118953915/206125946-43360ff0-9462-42b2-9df3-35a7db90d595.PNG">  
 My run:  
<img width="600" alt="lab2z" src="https://user-images.githubusercontent.com/118953915/206125962-e5eb007c-fe5b-4996-8491-7d67c11d25f7.PNG"> 
 
**Interesting optimisations**

Here is some special case:  
1. If looking at multiplexer:  
 <img width="600" alt="lab2za1" src="https://user-images.githubusercontent.com/118953915/206133157-cbc9abe7-19c8-400f-86f6-83da18aade6c.PNG">  
 (i) Explanation from training video:   
 <img width="600" alt="lab2za" src="https://user-images.githubusercontent.com/118953915/206132337-4969c59c-0cbb-48f9-99a7-da98f1b6a6c3.PNG">  
-When the number from the truth table convert to decimal value and times 2 and convert back to digital value, the pattern of output is the same for y[3:1] and then y[0]=0  
 (ii) Steps: yosys ; read_liberty -lib ../lib/sky*.lib ; read_verilog mult_2.v ; synth_top mul2 ; show  
 <img width="600" alt="lab2zb" src="https://user-images.githubusercontent.com/118953915/206185966-0bbfee96-fec1-49dc-a7d6-e43af9563009.PNG">  
 From the figure, we can see that there is no memories,no processor and no cell have been infferred. It is expected as show in (i), value y is from a and append with 1'b0.    
 Since there is no standard cell, 
 <img width="600" alt="lab2zc" src="https://user-images.githubusercontent.com/118953915/206187270-4f08db9e-bc3c-495c-ac67-d3746a534594.PNG">

2. Another multiplexer:  
 Explanation from training video:   
<img width="600" alt="lab2zd" src="https://user-images.githubusercontent.com/118953915/206198618-443bdc46-4601-4381-b3bf-5bc43ebf14f4.PNG">  
  (i) Steps: yosys ; read_liberty -lib ../lib/sky*.lib ; read_verilog mult_8.v ; synth_top mul8 ; show  
 Similar operation for mult_8 too  
 <img width="600" alt="lab2ze" src="https://user-images.githubusercontent.com/118953915/206199435-600e2f24-6ce4-4d7b-8380-211d5c1e2b7b.PNG">  
 💡 No hardware required for the special case show above, only rewiring the signal will do. Not required any std cell to obtain the logic functionality 
 
 
#
# Day_3 
**⭐Combinational and sequenial optimizations**


### *__Lecture Session__*

Synthesis is not a push-button solution, it is dependent on out design statement and clarity of implementation whether we want to optimize some particular places or not by setting ‘don’t touch’  
1. Optimization-minimizing cost functions: max delay cost(important!, weight in each path group-same clock constraint), min delay cost (expected-actual delay,unaffected by path group), max power cost, max area cost  
2. Constant propagation    
-Due to some requirement, there is 2 AND gate with one constant input “0”, so the output of the AND gate will directly obtain “0”, and depends on the another AND gate. While the another one have one constant input “1”, so the output only depends on one of the input, can directly understand as input A being wired as the output  
From training video:                          
![Picture1](https://user-images.githubusercontent.com/118953915/206745943-f7d65dae-7276-45a5-bc93-f7243e69371d.png)  
3. Combinational and sequential optimization  
-synthesis optimization for speed can be achieved through isolating the “and” portion of the circuit by assigning internal wire  
From training video:  
![Picture2](https://user-images.githubusercontent.com/118953915/206745950-9f696d1d-2ccd-4881-b51a-62a53861c83b.png)  
4. Another method: register retiming   
![Picture3](https://user-images.githubusercontent.com/118953915/206745951-1fc0c848-a096-4951-8491-90889fdcae33.png)  
5. Difference Among Constant propagation in :  
combinational logic is on Boolean Algebra  
sequential logic is on Boolean Algebra+Timing Diagram Analysis  (eg:timing in dff) 
> Boolean algebra table: https://www.electronics-tutorials.ws/boolean/boolean-algebra-simplification.html  
6. Additional optimization  
Resource sharing  
![Picture4](https://user-images.githubusercontent.com/118953915/206745954-fcf504ef-8667-40dd-8387-50d1ef777b46.png)  
-cons: increase in fanout  
 > Can refer this link: https://www.google.com/url?sa=i&url=https%3A%2F%2Fslideplayer.com%2Fslide%2F3480933%2F&psig=AOvVaw0SA_uGHPHqVw13ACSzU21j&ust=1670565262817000&source=images&cd=vfe&ved=0CBAQjRxqFwoTCIjmr9qq6fsCFQAAAAAdAAAAABAJ  
 
 -removal of un-connected logic across boundaries , removal of double inverting logic across boundaries, propagation of constants to reduce logic  
 
**(A) Introduction to optimization**

1. Combinational Logic Optimization – squeezing logic to get most optimised design -area & power saving  
Tech: constant propagation,boolean logic optimisation  
![Picture5](https://user-images.githubusercontent.com/118953915/206745955-a84d87f6-6b77-4353-a12f-e12a19f9b5c6.png)  
-Reduce to 2mos transistor-> less area and less power  
Example of sequential optimisation (boolean logic):  
 ![Picture6](https://user-images.githubusercontent.com/118953915/206745962-9a6bbcb7-37c1-4893-b9cf-cfbb370de588.png)  

2. Sequential Logic Optimization  
Tech: Sequential constan propagation, (advance: state optimisation,retiming,sequetial logic clonning)  
No hardware circuti required for below, since after optimization, it is getting y=1   
![Picture7](https://user-images.githubusercontent.com/118953915/206745967-d120b09d-83d1-42f7-bf60-882fba36aea0.png)  
However for this situation SET, the logic cannot being optimize due to Q=SET is not funtionally correct
-This is asynchronous dff, when the SET is ‘0’, the Q will wait for posedge clock to read in D   
![Picture8](https://user-images.githubusercontent.com/118953915/206745971-113bf5a6-34bf-41eb-83bf-ed9b8acb5ad7.png)  
State optimisation- optimize of unuse state (condense state machine)  
Cloning-physical aware synthesis (reduce large routing delay as shown in the figure below)  
Retiming both of the flop by reduce the logic at  1st combi and add those into 2nd combi, which can help in increase the frequency  operation of the circuit by reduce some delay in 1st combi  
![Picture9](https://user-images.githubusercontent.com/118953915/206745974-5ee450f6-9ad2-40c5-9c71-f5b75c655484.png)  

#### **Lab6: Combinational Logic Optimisations**  
 
Here is the contents of each opt_check:  
![Picture10](https://user-images.githubusercontent.com/118953915/206745982-59de4300-0cc6-4b0b-9aad-0b62add5ca10.png)  
For opt_check:  
Steps: yosys ; read_liberty -lib ../lib/sky*.lib ; read_verilog opt-check.v ; synth -top opt_check ; opt_clean -purge ; abc -liberty ../lib/sky*.lib  
![Picture11](https://user-images.githubusercontent.com/118953915/206745985-e3103002-9d2e-470b-b72c-e3a6294e7efc.png)  
While for the opt_check2:    
![Picture12](https://user-images.githubusercontent.com/118953915/206745987-eec5bf43-36f2-4c8e-9266-6504363c21ce.png) 
While for the opt_check3:   
![Picture13](https://user-images.githubusercontent.com/118953915/206745990-1ff6c1a3-3ca9-41f6-b67f-612e74b8bc96.png)  
While for opt_check_4:      
![Picture14](https://user-images.githubusercontent.com/118953915/206745994-ce09709f-ba4f-4189-be89-733f0c9dec3c.png)  
For multiple_module_opt.v:  
Before opt_clean -purge need flatten  
Steps: yosys ; read_liberty -lib ../lib/sky*.lib ; read_verilog multiple_module_opt.v ; synth -top multiple_module_opt ; flatten ; opt_clean -purge ; abc -liberty ../lib/sky*.lib  
![Picture15](https://user-images.githubusercontent.com/118953915/206745996-d373cc0b-782a-4f22-846f-e405e3ca537d.png)  
Addional info:
![Picture16](https://user-images.githubusercontent.com/118953915/206745999-34084cd2-0a79-4590-907a-a507089831ad.png)  
Previous(before optimize):  
<img width="570" alt="Capture" src="https://user-images.githubusercontent.com/118953915/206753157-86ceb110-234d-4be5-87dc-05084d22bde4.PNG">  
While for multiple_module_opt2:    
Steps: yosys ; read_liberty -lib ../lib/sky*.lib ; read_verilog multiple_module_opt2.v ; synth -top multiple_module_opt2 ; flatten ; opt_clean -purge ; abc -liberty ../lib/sky*.lib  
Here is the verilog:     
![Picture18](https://user-images.githubusercontent.com/118953915/206746011-e8c442cc-13a9-46c0-8e3a-05a11bf37e72.png)  
After optimize:   
![Picture19](https://user-images.githubusercontent.com/118953915/206746015-b9403176-1496-4ed8-930d-007567abc1c1.png)  
Previous (before optimize):   
![Picture20](https://user-images.githubusercontent.com/118953915/206746019-05c06841-3f11-4a9f-9e2d-2f401380271a.png)   
 
#### **Lab7: Sequential Logic Optimisations**

Explanation from training video:   
-The output(Q) of dff_const2 will always HIGH, so the optimisation can be done on this dff  
![Picture21](https://user-images.githubusercontent.com/118953915/206746020-43e47618-a922-4115-b63a-bcebf485a17d.png)  
Here is the waveform for dff_const1.v: 
 -Wait for next clock edge  
![Picture22](https://user-images.githubusercontent.com/118953915/206746024-a3782b6f-3fd0-4ec8-806e-c142dc6757af.png)  
Here is the waveform for dff_const2.v:    
-Output always HIGH   
![Picture23](https://user-images.githubusercontent.com/118953915/206746025-0199c2d2-50ea-4ee5-9a22-034570a1cebc.png) 
For const1.v & Const2.v:  
![Picture24](https://user-images.githubusercontent.com/118953915/206746026-677d49e5-4b6e-4a29-8896-2b44eea71c0d.png) 
Now, looking at dff_const2.v  
Here is the explanation from training video:  
![Picture25](https://user-images.githubusercontent.com/118953915/206746028-0601838d-336e-41ef-8fa4-4ebdc80074e2.png)
For dff_const3.v:     
![Picture25](https://user-images.githubusercontent.com/118953915/206746028-0601838d-336e-41ef-8fa4-4ebdc80074e2.png)    
Here is the waveform:
![Picture26](https://user-images.githubusercontent.com/118953915/206746031-a9663eeb-6635-4d40-8f0f-f2c539b08811.png)  
For dff_const4.v  
Here is the details:   
![Picture27](https://user-images.githubusercontent.com/118953915/206746035-500bfc65-73ea-4974-9325-d912002c73aa.png)  
Here is the details: 
![Picture28](https://user-images.githubusercontent.com/118953915/206746037-fef3eb9e-8317-4aad-ac36-cead4d573ef4.png)  
Here is the waveform:   
![Picture29](https://user-images.githubusercontent.com/118953915/206746039-d0505376-74e3-4a75-91a7-4d6a2aafcc8f.png)  
For dff_const4.v:      
![Picture30](https://user-images.githubusercontent.com/118953915/206746042-adea7672-ea04-45a7-97af-ed6759f16253.png)  
For dff_const5  
Here is the details:  
![Picture31](https://user-images.githubusercontent.com/118953915/206746046-b10f71c6-8a7d-4fef-95af-760457547ca7.png)  
Here is the waveform:   
![Picture32](https://user-images.githubusercontent.com/118953915/206746048-cf3cc483-65ba-4efa-9bba-c77935007821.png)
For dff_const5.v:  
 ![Picture33](https://user-images.githubusercontent.com/118953915/206746057-02bcf9cf-acab-4db9-a9f3-bdd6439c71b1.png) 

**Unused Output Optimization**
 
Here is the explanation from training video:  
![Picture34](https://user-images.githubusercontent.com/118953915/206746059-4f022587-fb41-4eaf-9a7a-0920248bac28.png)  
Here is the counter_opt:  
![Picture35](https://user-images.githubusercontent.com/118953915/206746061-58a2b0a6-8fe4-47ab-9069-70b28cb3885c.png)
Remodified the file to look for 3 dff:  
![Picture36](https://user-images.githubusercontent.com/118953915/206746066-8c2d932b-36f2-45c7-b6d6-c086b166d449.png)
![Picture37](https://user-images.githubusercontent.com/118953915/206746071-ab02105c-d9cb-4d5a-92a0-b2bf4fccb585.png)  
💡In previous counter_opt, all those logic not having a direct role in determining the primary output of the module will optimize directly
