*Türkçe versiyon için [README.md](README.md) dosyasına bakabilirsiniz.*

# Basic Computer Simulation

This project contains a Basic Computer simulation designed using **basic logic gates and integrated circuits (ICs)** in the Proteus environment. It serves as a great example for understanding basic computer architecture and the operating logic of processors.

## Core Components (ICs) Used in the Project

The project is built with standard 74LS series logic ICs and memory units commonly used in real-world applications:

- **74LS181 (ALU - Arithmetic Logic Unit):** The heart of the computer. It performs mathematical and logical operations such as addition, subtraction, logical AND/OR.
- **74LS173 (4-bit D-Type Registers):** Used for temporary data storage. They typically serve as the Accumulator (A Register), B Register, Instruction Register, or Output Register.
- **74LS161 (Synchronous 4-bit Counter):** Used as the Program Counter (PC), keeping track of which instruction to execute next from the memory (RAM/ROM).
- **74LS138 (3-to-8 Decoder):** Used for address decoding or decoding instructions to generate the corresponding control signals (Control Word).
- **74LS245 (Octal Bus Transceiver):** Allows units to communicate with the common Data Bus and controls the direction of data flow.
- **RAM (Random Access Memory):** The main memory unit where program instructions and data are stored.
- **Logic State & Logic Probe:** Used to manually input "1" or "0" signals into the circuit from the outside (e.g., inputting data or testing control signals) and to observe signals on the lines.

## How to Perform Addition and Subtraction?

Operations like addition and subtraction on the simulation are primarily performed by the **74LS181 ALU (Arithmetic Logic Unit)**. If the processor operates fully automatically (with a Control Unit), a small program is written into the RAM. If it's in manual mode (controlled by Logic State switches), the following steps are taken:

### 1. Addition (A + B)
1. **Loading Data:** Put the first number to be added onto the Data Bus and save it to the **Accumulator (A Register)** (by activating its Load signal).
2. **Loading the Second Data:** Put the second number onto the Data Bus and save it to the **B Register**.
3. **ALU Setup:** Set the control pins (S0, S1, S2, S3, and M) of the 74LS181 IC to **ADD** mode.
   - *Note: For the 74LS181, addition is usually performed when `M=0` (Arithmetic operation) and the Select (S) pins are set to `S3 S2 S1 S0 = 1001` (A+B).*
4. **Viewing the Result:** The ALU's outputs will provide the sum of the two numbers. You can optionally route this result back to a register or directly to an output display.

### 2. Subtraction (A - B)
1. **Loading Data:** Save the first number (the minuend) into the **Accumulator (A Register)**.
2. **Loading the Second Data:** Save the number to be subtracted (the subtrahend) into the **B Register**.
3. **ALU Setup:** Set the control pins of the 74LS181 IC to **SUBTRACT** mode.
   - *Note: For the 74LS181, subtraction (A-B) is usually performed by setting `M=0` and the Select pins to `S3 S2 S1 S0 = 0110`.*
4. **Viewing the Result:** The result (A-B) is generated at the ALU output. This value can be transferred to the relevant unit via the data bus.

## How to Run?
1. Ensure that the **Proteus** software is installed on your computer.
2. Clone or download this repository to your computer.
3. Open the project in Proteus by double-clicking the `BasicComputer.pdsprj` file.
4. Start the simulation by pressing the **Play** button in the bottom left corner.
5. You can change signals to 1 or 0 by clicking the `Logic State` buttons (red/blue squares) and observe the circuit's response via the `Logic Probe` or LEDs.
