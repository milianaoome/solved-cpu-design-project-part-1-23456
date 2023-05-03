Download Link: https://assignmentchef.com/product/solved-cpu-design-project-part-1-23456
<br>
<p class="ui header product-top-header" title="CPU Design Project: Part 1 ,2,3,4,5,6 Solution">CPU<strong> Design Project  </strong>

A RISC CPU is to be designed in the VHDL modeling language, verified via the Mentor Graphics “ModelSim” or Aldec “Active-HDL” simulator, and implemented on the Altera DE2 FPGA board using Altera’s Quartus II software.  The project consists of six parts as defined below. Due dates will be listed above as the semester progresses. You read problem definitions of all six parts before actually starting with Part 1, i.e., Instruction Set Architecture (ISA). Please submit only the List Format (do not submit wave format) of the simulation results in part 3, part 4, and part 5. Always annotate your simulation results. Maintain a single folder for submitting the project parts. When submitting a later part, all the previous parts need to be in the folder.

<strong>CPU Design Project: Part 1 – ISA, Report </strong>

You are to design an instruction set architecture (ISA) for a new 16-bit microprocessor (μP). The μP will be designed and modeled in VHDL in later parts. Your ISA is to be designed using RISC design principles, with the primary design goals being low cost and a minimal number of clock cycles per instruction. Following are the requirements for your ISA.

1.      The ISA may contain no more than 16 unique instructions. However, you may have multiple formats for a given type of instruction, if necessary.

2.      Of the 16 instructions, at least one instruction should make your processor HALT.

3.      The ISA is to support 16-bit data words only. (No byte operands.)

a. All operands are to be 16-bit signed integers (2’s complement).

b. Each instruction must be encoded using one 16-bit word.

4.      The ISA is to support linear addressing of 1K, 16-bit words memory. The memory is to be word-addressable only – not byte-addressable.

5.      The ISA should contain appropriate numbers and types of user-programmable registers to support it. Since this is a small processor, the hardware does not necessarily need to support dedicated registers for stack pointer, frame pointer, etc.

6.      The ISA must “support” the following C Programming Language constructs:

·      Assignment operator: variable = expression;

–          Supported arithmetic operators in expressions must include: add (+) and subtract (-)

o   It is not necessary to support multiply (*) and divide (/)

–          Supported logical operators in expressions must include: and (&amp;) and or (|)

–          Data are limited to:

o   16-bit two’s-complement integers (Example: int a;)

o   One-dimensional integer arrays (Example: int a[10];)

·      Control flow structures: “if-else” structures, “while” loops, “for” loops

–       These should support the six standard relational operators:

==, !=, , &lt;=, &lt;, =

·      Functions (call and return), with parameters able to be passed by value or by reference.

7.      Provide the following information about your ISA:

·          List and describe the roles of the user-programmable registers.

·          List and describe the different instruction formats used.

·          For each instruction in your instruction set, list the following:

·         Assembly language for each form of the instruction – mnemonic and operands

·         Machine language for each form of the instruction: instruction code format, op-code, and operand encoding

·         Justification for including each form of the instruction in your ISA

8.      For each C construct listed in item 6 above, provide an example showing how the construct would be “compiled”, i.e. implemented with your instruction set, by writing an example of the C construct and the corresponding assembly language implementation.

<strong> CPU Design Project: Part 2 – Datapath, Report </strong>

In this part, you are to design the datapath of a CPU that will realize the instruction set architecture (ISA) designed in the previous part (including any “adjustments” made to the ISA). Include the following in your report.

1.      A register-level block diagram of the datapath, with all components and control signals clearly labeled.

2.      External to the CPU, your block diagram should also show connections to the system memory (Von Neumann architecture) or memories (Harvard architecture). These memory components are not part of the CPU design, but since data and instructions move between the CPU datapath and the system memory, it is important to account for the datapath’s interface to the memory/memories.

3.      A description of the inputs, outputs, and function of each component in the datapath.

4.      For each instruction of your ISA, list the register transfers, or sequence of register transfers, required to fetch and execute the instruction. Register names should correspond to components in your datapath diagram.

5.      For single-cycle and pipelined datapaths, create a truth table listing all control signals and the values of each control signal required for executing each instruction in your ISA. For multicycle datapath, create a state diagram, and also a state table listing all control signals and the values of each control signal corresponding to the different states (like fetch, decode, ALU operation, etc) in your diagram. (Note that in state like “ALU operation”, the control signals may vary depending on different opcodes.)

6.      A discussion of the tradeoffs and other design decisions made in developing your datapath. This should include:

·         Cost vs. speed tradeoffs that you considered.

·         Why you chose a single-cycle, multi-cycle design or pipeline datapath.

·         Decisions related to “shared” and/or “dedicated” components.

·         Selection of edge-triggered vs. latching registers.

·         Other decisions that were considered.

Major Datapath Components Likely to be needed:

1        ALU: The ALU must provide all arithmetic and logic functions required to support your instruction set. It should not provide unnecessary functions.

2        Register file: Design as a multi-port “memory array”. DO NOT instantiate individual registers.

3        Sign/zero extension logic, as appropriate, for ALU inputs.

4        Program counter (PC). PC should be a simple register.

5        Instruction register (IR) (if required).

6        Assorted multiplexers for data paths and register address inputs.

<strong>CPU Design Project: Part 3</strong>

Datapath components and control unit implementation

Develop and verify the VHDL model for each unique component within your datapath. Also, design and test a VHDL “behavioral” model of the control unit to realize the behavior described in your control signal table in part 2, including any instruction decoding. Thoroughly simulate the control unit and each component individually. Guaranteeing the correct functioning of each component is very important since the control unit and all components will be connected in the next part to form a top-level component. Any failing component will induce the malfunctioning of the top-level module.

To facilitate debugging on the Altera FPGA board, the datapath needs an additional 4-bit input named “inr” used with a multiplexer to select one of your CPU registers, with a 16-bit output named “outvalue” to display the value of the selected register. These two ports will be part of the primary inputs and primary outputs of the final CPU. These two ports are added to help us correctly implement our CPU all the way through this project. In the simulation phase, they are used to help us decide whether we get the correct results saved in the correct register. In the experiment phase, these two ports are used to display the content of target register on the FPGA board to demonstrate the correct execution of your program. In real CPU, we don’t have these two ports. They are only used to help us implement this project.

For single-cycle and pipeline datapath, the lecture slides show separate instruction memory and data memory. If your datapath uses a separate data and instruction memory, you can actually write a VHDL model of your own instruction memory and leave the data memory to be generated from Alera’s Megafunction library in part 5. In this way, it will be easier for you to simulate a small program in part 4. Of course, you can also leave both memories to be generated in part 5. In this way you will have to manually supply each instruction to the datapath in part 4. If your design is multi-cycle datapath, you can leave your memory to be generated in part 5, or write a VHDL model of a memory to be used to help test part 4.

Notes:

1.      Refer the LeonardoSpectrum for Altera HDL Synthesis Guide to write the VHDL code according to the synthesis guidelines so that in the final stage, your design is synthesized correctly by the FPGA.

2.      For every sequential component within your datapath, you will need an input “reset” signal to establish initial states.

3.      The VHDL model is to be a register-transfer-level (RTL) design (not gate level).

4.      Design and test VHDL models of each unique component.

5.      Submit all VHDL code. Submit all simulation results and clearly annotate each simulation results.

<strong>CPU Design Project: Part 4-Datapath Verification,</strong>

Combine all the components created in part 3 together into a new top-level component which will include both datapath and the control unit connected to each other (also include the instruction memory in your datapath if you have created it in part 3). This top-level component will be very similar to the final CPU you are going to create in part 5 except the memory.

The top-level component must be capable of working with at least a single memory outside the CPU. So it must have at least three 16-bit external “ports” to connect the component to the memory: a Read data bus (16-bit), A Write data bus (16-bit) and an address bus (10-bit). For these who have separate data and instruction memory in the datapath, if you have created an instruction memory in part 3, you will just need one more data memory. Otherwise, you will need two memories (both instruction and data memory) to use in logic simulation. The memory you need will be added in Part 5, which will be the RAM block in the Altera Megafunctions Library.

Verify this top-level component as described in the block diagram and register transfers in Part 2. Write a testbench to verify the correct execution of each instruction in your ISA (except the instructions which need data memory access, like “lw” and “sw”). Show in the simulation where you verified each required register transfer for the CPU. (If some register transfers are common to multiple instructions, you do not need to show them separately for every instruction – but it might be a good idea to do so anyway.)  After that, write a short program using your instruction set (containing all kinds of instructions except “lw” and “sw”), hand compile the chosen test program into binary code and then use this code to verify if your datapath gives you the expected results.

Think about it, can you verify execution of “lw” and “sw” instruction in this part? If yes, how?

Notes:

1.      The top-level design should contain only component instantiations, matching your block diagram (changes may be made to the diagram as necessary).

2.      In the simulation, if you have included the instruction memory in your datapath, you can place instructions in the instruction memory to do simulation. Otherwise, you need to supply instruction(s) to the datapath manually in the testbench.

3.      You are to submit the following in your notebook:

a)    The VHDL code of the top level component.

b)    Simulation results showing correct execution of each instruction and also the short test program. Clearly label the important information on the simulation results.

c)    Both the assembly code and the binary code of the test program you used.

<strong> CPU Design Project: Part 5 – Final CPU</strong>

Now, complete the system design by adding Altera memory modules, and write a test program that contains all kinds of instructions in your ISA – including tests of different options for each instruction (ex. branches taken and not taken). Since the Altera memories were not previously used in Part 4, verify the correct execution of your test program, including any “lw” and “sw” instruction.

A 16-bit memory module must be created from Altera’s Megafunction Library, as explained in ‘Run time content editable memory tutorial’ file (posted on course website). This will ensure that RAM blocks in the Altera FPGA are used for system memory, rather than an array of discrete flip flops. For students who use separate instruction and data memories: If you have written an instruction memory model for use in Modelsim/Active-HDL, you should also generate a data memory in this part, in addition to the program memory, with one for storing the test program and the other for storing data.

As explained on page 5 of the tutorial, you will need the supplied RAM_init.mif file (a “memory initialization file”). What’s written in the “.mif” file will automatically be loaded into the designated addresses of the generated Altera memory at the start of simulation. So any 16-bit word can be placed in any cell of the memory by modifying the RAM_init.mif file. For example, you can modify the given RAM_init.mif file according to the binary code of your test program. You can also put some data in some cells of the memory. A .vhd file and the RAM_init.mif file will be created in your working directory.

Include the memory.vhd file created above in your datapath. Create the final CPU component by instantiating and connecting the memory to the top-level component created in part 4, or else include the memory within the top-level component. At the top-most level, CPU I/O ports should be limited to a clock, reset, and inr as the input ports, and outvalue as the output port. Submit the VHDL models of the memory and the final CPU.

Manually compile the test program into binary code, with the binary code loaded into memory via the RAM_init.mif file described above. Submit and annotate the simulation results. To minimize the length of the simulation listing for the simulation of the test program, you can limit the display to one line per clock transition (i.e., trigger only on clock signal transitions). Show a sufficient set of control signals to demonstrate correct operation of each instruction (control unit state, address bus, data bus, ALU output, register file outputs, register file input, memory control signals, etc.) On the simulation listing, annotate by writing the corresponding assembly language instruction next to each execute cycle and highlighting the “significant” result register or bus value.  Also submit the assembly language listing for your test program.

<strong> CPU Design Project – Part 6 – Hardware Implementation and a Working Processor Demo</strong>

1)      Follow the Altera Quartus II and DE2 Manual (posted on course website) for designing and implementing your circuit on the FPGA.

2)      Reset can be connected to any of the 4 Keys on DE2 Board. These Keys are normally at logic ‘1’. And pressing them will change the logic to ‘0’. So make the changes in your design as needed.

3)      Clock can be connected to any of the two free-running clock frequencies available, 27MHz and 50MHZ. To connect to any of these clock inputs, the pin numbers are mentioned in the Pin Assignment MSExcel sheet. You can also debug your design by connecting the clock to one of the manual keys on the DE2 board, manually creating clock pulses instead of using free-running clock.

4)      The “inr” input that selects the register number can be connected to any 4 switches on the board. And the “outvalue” that displays the contents of the register selected, can be connected to the LEDs or LCD on the board. For using 7 segment displays on the board you will require a HEX to 7 segment conversion model provided on the course website.

5)      Run the test program and verify the results with your simulation in part 5.

6)      You will have to show the implemented design on your DE2 Board. You will be conducting a demo as follows:

(a)        Briefly describe what is implemented, what program you will run and what result is expected.

(b)       Run the program pointing to the functions of the buttons you press. Let the viewer examine the result.

(c)        Offer to make a change to some parameter to a viewer selected value and rerun the demo.

(d)       Total duration of demo: FIVE MINUTES.

7)      Part 6 report must be a one-page reply to three questions:

(a)       What did you learn from this project?

(b)       What would you do differently next time?

(c)        What is your advice to someone who is going to work on a similar project?

(d)       Email report to <a href="/cdn-cgi/l/email-protection" class="__cf_email__" data-cfemail="b2c7d8d8c5d3de9cd5c7dbdcf2d3c7d0c7c0dc9cd7d6c7">[email protected]</a>