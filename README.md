                            SCALAR PIPELINE SIMULATOR

        Overview:

        This program simulates an instruction pipeline for a processor. It includes stages such as ->fetch
        ->decode
        ->execute
        ->memory
        ->writeback
        The pipeline is designed to handle various types of instructions and their execution involving two kinds of hazards which are Read after write hazard(data hazard) and Control hazard.

        Input Files:
      
        main.cpp: Contains the main logic for the instruction pipeline simulation.
        ICache.txt: Input file containing instructions to be fetched.
        DCache.txt: Input file containing data for memory operations.
        RF.txt: Input file containing register values.

        The program will read instructions from ICache.txt, data from DCache.txt, and initial register values from RF.txt. It will then simulate the instruction pipeline and generate output files.

        Description:

        Fetch Stage:
        ->The fetch stage is responsible for retrieving the next instruction to be executed from memory.
        ->The instruction is fetched from memory and loaded into a temporary register for further processing.
        ->During this stage, the PC is incremented or updated to point to the address of the next instruction.
        
        Decode Stage:
        ->In the decode stage, the fetched instruction is analyzed and decoded to determine its type and required operations.
        ->The instruction's opcode (operation code) is extracted to identify the type of instruction, such as arithmetic, logical, memory access, or control flow.
        ->Depending on the instruction type, the decode stage sets up the appropriate control signals and prepares operand values for the execution stage.
        ->For instructions involving registers or memory addresses, the decode stage identifies the specific registers or memory locations involved in the operation.
        

        Execute Stage:
        ->The execute stage is where the actual computation or operation specified by the instruction takes place.
        ->Control signals generated in the decode stage guide the ALU to perform addition, subtraction, bitwise operations, etc., on the operand values obtained from registers or immediate values.
        ->For instructions like branches or jumps, the execute stage evaluates conditions and updates the Program Counter accordingly to alter the program flow.
       

        Memory Stage:
        ->In this stage, instructions that involve memory access are executed.
        ->This stage includes loading data from memory or storing data to memory.
        
        Writeback Stage:
       ->The writeback stage finalizes the instruction execution by updating the register file with the result.
        
        Handling Hazards:

        Data Hazard (RAW - Read After Write):
        ->Data hazards occur when an instruction depends on the result of a previous instruction that has not yet been written back to the register file. This situation can lead to incorrect results if not handled properly.
        ->The code implements data hazard handling by introducing stalls. Stalls are essentially "no-operation" instructions that do not perform any meaningful operation but serve to delay the pipeline execution.
        ->This is typically achieved by monitoring dependencies between instructions, such as checking if the operands of an instruction are being modified by a previous instruction that has not yet completed its writeback stage.

        Control Hazard:
        -> Control hazards occur when the next instruction to be executed depends on the result of a previous instruction whose outcome is not yet known. This commonly occurs with branch instructions where the execution path depends on a condition that is determined during execution state in the pipeline.
        ->The code handles control hazards by introducing stalls to prevent incorrect execution due to branches.


        Compilation:

        ->Compile the program using a C++ compiler using the following commands(For Windows).
            
            g++ main.cpp
            ./a.exe


        Output Files:
        ->Output.txt: Contains simulation results including the number of instructions executed, instruction classes, cycles per instruction, and stall information.
        ->DCache.txt: Contains updated data after memory operations.
        

        *Output.txt and DCache.txt should be present in Output folder beforehand.




