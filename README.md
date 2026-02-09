# 4-Bit Ripple Carry Adder Circuit Design Using Logisim

## Aim
To design, simulate, and verify the working of a 4-bit Ripple Carry Adder (RCA) circuit using Logisim software and validate its operation through binary addition rules.

## Materials/Resources Needed

### Software
- **Logisim** (digital logic circuit simulator)
- Compatible with Windows, macOS, and Linux operating systems

### Circuit Components (in Logisim)
- XOR gates
- AND gates
- OR gates
- Input pins (8 for data inputs, 1 for carry-in)
- Output pins (4 for sum, 1 for carry-out)
- Wires/connectors
- Text labels (for documentation)
- LEDs (for output visualization)

## Theory

### 4-Bit Ripple Carry Adder (RCA)
A Ripple Carry Adder is a digital circuit that produces the arithmetic sum of two 4-bit binary numbers. It is constructed by cascading four Full Adders (FA) in series. The carry-out of each full adder is connected to the carry-in of the next higher-order full adder.

- **Inputs**: 
  - Number A: A3, A2, A1, A0
  - Number B: B3, B2, B1, B0
  - Carry-in (Cin): Usually set to 0 for simple addition
- **Outputs**:
  - Sum: S3, S2, S1, S0
  - Carry-out (Cout): The final carry bit from the Most Significant Bit (MSB)



**Working Principle:**
Each stage of the ripple adder is a Full Adder. A Full Adder adds three bits: two significant bits and a carry bit from a previous stage. The "ripple" effect occurs because the carry bit of each stage must be calculated before the next stage can provide a correct sum.

**Key Equations:**
Sum = A ⊕ B ⊕ Cin Cout = (A · B) + (Cin · (A ⊕ B))
**Full Adder Truth Table:**

| A | B | Cin | Sum | Cout |
|---|---|-----|-----|------|
| 0 | 0 | 0   | 0   | 0    |
| 0 | 0 | 1   | 1   | 0    |
| 0 | 1 | 0   | 1   | 0    |
| 0 | 1 | 1   | 0   | 1    |
| 1 | 0 | 0   | 1   | 0    |
| 1 | 0 | 1   | 0   | 1    |
| 1 | 1 | 0   | 0   | 1    |
| 1 | 1 | 1   | 1   | 1    |

## Procedure

### Part A: Full Adder Sub-circuit
1. **Launch Logisim** and create a new circuit named "Full_Adder".
2. **Add Logic Gates:** - Place two XOR gates, two AND gates, and one OR gate.
3. **Connect Inputs/Outputs:** - Create three input pins (A, B, Cin) and two output pins (Sum, Cout).
4. **Wire the Logic:** - XOR A and B, then XOR that result with Cin to produce the Sum.
   - AND A and B; AND the first XOR result with Cin.
   - OR the two AND results to produce Cout.
5. **Save the Circuit.**

### Part B: 4-Bit Ripple Carry Adder
1. **Create New Circuit** named "4Bit_Adder".
2. **Add Sub-circuits:** Drag and drop 4 instances of your "Full_Adder" into the workspace.
3. **Add Input Pins:**
   - Place 4 pins for Number A (A3-A0) and 4 pins for Number B (B3-B0).
   - Place 1 pin for the initial Cin.
4. **Connect the Ripple Chain:**
   - Connect initial Cin to the first Full Adder (FA0).
   - Connect Cout of FA0 to Cin of FA1.
   - Connect Cout of FA1 to Cin of FA2.
   - Connect Cout of FA2 to Cin of FA3.
5. **Connect Outputs:**
   - Place 4 output pins/LEDs for the Sum bits (S3-S0).
   - Place 1 output pin/LED for the final Cout.
6. **Test the Circuit:**
   - Use the "Poke" tool to toggle inputs.
   - Verify that adding 0101 (5) and 0011 (3) results in 1000 (8).

## Results

### 4-Bit Ripple Carry Adder Verification
The 4-bit Ripple Carry Adder circuit successfully performed binary addition. Testing validated:
- **Summation Accuracy:** Adding two 4-bit numbers produced the correct binary sum.
- **Carry Propagation:** When a carry was generated in the LSB (e.g., 0001 + 0001), it correctly "rippled" to the next bit.
- **Maximum Value:** Adding 1111 (15) and 1111 (15) with Cin=0 resulted in Sum=1110 (14) and Cout=1 (representing 30 total).
- **Initial Carry:** Activating the initial Cin added 1 to the total sum as expected.

The circuit demonstrated correct logic functionality and matched the expected results of manual binary addition.

## Key Differences

| Feature | Half Adder | Full Adder (Single Bit) | 4-Bit Ripple Carry Adder |
|---------|------------|-------------------------|--------------------------|
| Inputs  | 2 Bits     | 3 Bits (A, B, Cin)      | 9 Bits (Two 4-bit + Cin) |
| Outputs | 2 (S, C)   | 2 (S, Cout)             | 5 (Four Sum + Cout)      |
| Cascade | No         | Yes                     | Yes (to 8-bit, 16-bit)   |
| Logic   | Basic      | Medium                  | Complex (Modular)        |

## Applications

### Ripple Carry Adder Applications:
- Arithmetic Logic Units (ALUs) in microprocessors
- Digital signal processing (DSP)
- Calculator logic for basic addition
- Memory address calculation in CPUs
- Program counters for incrementing instructions

## Conclusion
The 4-bit Ripple Carry Adder was successfully designed and simulated using a modular approach in Logisim. By cascading four full-adder circuits, the design effectively managed carry bits through each stage of addition. This project confirms that the ripple carry architecture, while simple, is a foundational element in digital arithmetic design.
