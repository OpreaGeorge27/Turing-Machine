# Morse Code Decoder - Turing Machine Implementation

## Project Overview
This project implements a Turing machine for decoding Morse code and identifying key words in the resulting text.

## Author
- **Oprea George**
- Class: 324CBa
- Project: Tema1-AA-Masina Turing-Decodificator Morse

## Implementation Details

### Translation Mechanism
The Turing machine implemented in the `morse.tms` file operates as follows:

1. **Initial State (q0)**: 
   - Traverses the entire input string
   - Adds an '=' character at the end of the string
   - Transitions to state q1

2. **Positioning State (q1)**:
   - Returns to the beginning of the string
   - Transitions to state q2 to begin reading

3. **Reading State (q2)**:
   - Starting state for reading a new sequence of characters
   - Each character is stored in a unique state for each possible combination (e.g., '..-' = state ppl)
   - When the machine encounters a '*' character, it decodes the state into the specific letter
   - Transitions to a specific state (SC_A, SC_B, SC_C...) for each letter

4. **Character Writing**:
   - Machine moves to the end of the string (marked by '=')
   - Transitions to the letter state (A, B, C, D...)
   - Bypasses any letters already written
   - Writes the letter on the tape when it finds an empty space
   - Transitions to state q3

5. **Cleanup State (q3)**:
   - Returns to the beginning of the tape to erase the previously decoded sequence
   - Transitions to state q4

6. **Erasure State (q4)**:
   - Erases all characters until it encounters the '*' character
   - Transitions back to state q2 to read the next sequence

### Keyword Detection
After translating the input string, the machine:

1. Positions at the beginning of the translation
2. Transitions to the START_CAUTARE state
3. When it finds an 'H' or 'S' character, it enters the GH/GS state and continues
4. If it finds 'E' or 'O', it transitions to GHE/GSO and so on until it finds each letter of the keyword
5. If it finds the '/' character (word separator), the machine returns to the START_CAUTARE state

## State Descriptions
- **q0**: Moves to the end to add an '=' character
- **q1**: Returns to begin reading
- **q2**: Begins reading and stores what it reads (e.g., '..-' = state ppl)
- **Special states**: Decodes into specific combinations (S_A, S_B, S_C...) and moves until after '='
- **Letter states**: A, B, C, D... to write the letter at the end of the string
- **q3**: Returns to erase the previously read letter
- **q4**: Erases the read letter and returns to q2