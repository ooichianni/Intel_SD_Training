create_clock -name MYCLK -per 10 [get_ports clk]

set_clock_latency -source 2 [get_clocks MYCLK]
set_clock_latency  1 [get_clocks MYCLK]
set_clock_uncertainty -setup 0.5 [get_clocks MYCLK]
set_clock_uncertainty -hold 0.1 [get_clocks MYCLK]

set_input_delay -max 5 -clock [get_clocks MYCLK] [get_ports IN_B]
set_input_delay -max 5 -clock [get_clocks MYCLK] [get_ports IN_A]
set_input_delay -min 1 -clock [get_clocks MYCLK] [get_ports IN_A] 
set_input_delay -max 5 -clock [get_clocks MYCLK] [get_ports IN_A]

set_input_transition -max 0.3 [get_ports IN_A]
set_input_transition -max 0.3 [get_ports IN_B]
set_input_transition -min 0.1 [get_ports IN_A]
set_input_transition -min 0.1 [get_ports IN_B]

set_output_delay -max 5 -clock [get_clocks MYCLK] [get_ports OUT_Y]
set_output_delay -min 1 -clock [get_clocks MYCLK] [get_ports OUT_Y]

set_load -max 0.4 [get_ports OUT_Y]
set_load -min 0.1 [get_ports OUT_Y]

report_port -verbose
report_timing -to IN_A -net -trans -cap -nosplit -delay_type min
report_timing -to IN_A -net -trans -cap -nosplit

create_generated_clock -name MY_GEN_CLK -master MYCLK -source [get_ports clk] -div 1 [get_ports out_clk]

set_clock_latency -max 1 [get_clocks MY_GEN_CLK]
set_output_delay -max 5 [get_ports OUT_Y] -clock [get_clocks MY_GEN_CLK] 
set_output_delay -min 1 [get_ports OUT_Y] -clock [get_clocks MY_GEN_CLK] 

set_max_latency 1.0 -from [get_ports IN_C] -to [get_ports OUT_Z]
set_max_latency 1.0 -from [get_ports IN_D] -to [get_ports OUT_Z]

Create_clock –name My_VCLK –period 5 
set_output_delay -max 2.5 -clock MY_VCLK [get_ports OUT_Z]
set_input_delay -max 1.5 -clock MY_VCLK [get_ports IN_C]
set_input_delay -max 1.5 -clock MY_VCLK [get_ports IN_D]

set_input_delay –max 2 –clock CLK [get_ports IN_A]
set_input_delay –max 3 –clock CLK –clock_fall –add [get_ports IN_A]

set_output_delay -max 2 -clock CLK [get_ports Out_Y]
set_output_delay -max 3 -clock CLK -clock_fall -add [get_ports Out_Y]

set_max_delay 0.1 -from [all_inputs] -to [get_port OUT_Z]

create_clock -name MYVCLK -per 10
set_input_delay -max 5 [get_ports IN_C] -clock [get_clocks MYVCLK]
set_input_delay -max 5 [get_ports IN_D] -clock [get_clocks MYVCLK]
set_output_delay -max 4.9 [get_ports OUT_Z] -clock [get_clocks MYVCLK]
