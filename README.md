# PIPELINEPROCESSORDESIGN

COMPANY :CODTECH IT SOLUTIONS

NAME :SARUMATHI M

INTERN ID :CT04DH923

DOMAIN: VLSI

DURATION: 4 WEEKS

MENTOR : NEELA SANTOSH

discription:
PipelinedProcessor1 is a verilog and PipelinedProcessor2 is testbench runed in EDA playground.
       
The 4-stage pipelined processor implemented here is designed to execute simple instructions like ADD, SUB, and LOAD using a sequential flow of stages: Instruction Fetch (IF), Instruction Decode (ID), Execute (EX), and Write Back (WB). Pipelining allows these stages to work in parallel, improving instruction throughput compared to a single-cycle processor. In our design, instructions are stored in a small instruction memory (instr_mem), and a simple register file (regfile) is used to store the results. Each clock cycle moves the data and control signals forward from one stage to the next using pipeline registers.

The processor uses a 2-bit opcode to determine which operation to perform. For example, 00 represents ADD, 01 represents SUB, and 10 represents LOAD. Each instruction is stored as an 8-bit value, with the top 2 bits representing the opcode and the lower 6 bits representing an immediate data value (e.g., 5 or 9). In the Instruction Fetch (IF) stage, the current instruction is fetched from instr_mem using the program counter (pc). This instruction is then passed to the next stage through a pipeline register (IF_ID_instr).

In the Instruction Decode (ID) stage, the opcode and data fields are separated. The processor reads the operand from the register file (here regfile[0]) and stores the decoded values in the ID/EX pipeline registers (ID_EX_op, ID_EX_A, and ID_EX_B). The Execute (EX) stage performs the arithmetic or load operation based on the opcode. For ADD, the two operands (register value and immediate) are added; for SUB, subtraction is performed; and for LOAD, the immediate value is directly assigned as the result. The output of this stage is stored in the EX/WB pipeline register (EX_WB_result).

Finally, in the Write Back (WB) stage, the result computed in EX is written back into regfile[0] and simultaneously assigned to the result output signal. This ensures that the final value can be observed externally, and subsequent instructions can use it as an operand.

The testbench (tb_pipeline_processor) verifies this processor design by providing a clock signal with a 10 ns period and a reset signal. The $dumpfile and $dumpvars commands are used to create a dump.vcd file, which allows waveform viewing in EPWave on EDA Playground. The $monitor statement continuously prints the output result with simulation time. When simulated, the pipeline executes the three predefined instructions (ADD 5, SUB 2, LOAD 9) in a pipelined fashion, and the result output changes as each instruction completes its write-back stage.
OUTPUT:

<img width="1365" height="638" alt="Image" src="https://github.com/user-attachments/assets/e90ce0d8-5ffe-4a56-ba8f-7e80eb9c6180" />

<img width="1328" height="627" alt="Image" src="https://github.com/user-attachments/assets/5d995eaf-5a34-4351-9993-e7c3d4fd8431" />
