# Digital-Voting-machine-DLD-Project
Circuit implementation that digitally counts votes for each candidate and show who has more votes and winner for Election

Table of Contents

i.	Introduction
ii.	Problem Analysis 
iii.	Design Requirements 
iv.	Feasibility Analysis 
v.	Possible Solutions 
vi.	Preliminary Design 
vii.	Design Description 
viii.	Software Simulation 
ix.	Experimental Results
x.	Performance Analysis 
xi.	Future Scope 
xii.	Social and Cultural Implications 
xiii.	Conclusion 
xiv.	References 








1. Introduction
  
A Digital Voting Machine (DVM) is an electronic system designed to conduct secure and efficient voting. The purpose of this project is to implement a voting system using Digital Logic Design concepts such as logic gates, multiplexers, and decoders.
This system ensures one-person-one-vote by preventing multiple votes using control logic. It replaces traditional manual voting systems, making the process faster, more reliable, and less prone to human error. The project uses combinational logic circuits to verify votes and count them accurately.
  

2. Problem Analysis

The main problem is to design a voting system that:
•	Allows only one valid vote at a time 
•	Prevents multiple voting attempts 
•	Selects candidates correctly 
•	Displays the result accurately 
The challenge is to implement all these features using basic digital components like NAND, NOR gates, multiplexers, and decoders.



3. Design Requirements

The system must include:
•	Inputs: Voter button signals, mode selection (admin/voting) 
•	Outputs: Vote count for each candidate 
•	Components: 
o	NAND & NOR gates (for protection logic) 
o	2×1 Multiplexer (mode selection) 
o	4×1 Multiplexer (candidate selection) 
o	Decoder (to activate candidate lines) 
o	Counters using D flip-flops (for counting of votes).
o	BCD to 7-segment and 7-segment display. 
Constraints:
•	Only one vote per user 
•	No overlapping signals 
•	Accurate counting


4. Feasibility Analysis

This project is feasible because:
•	Cost: Uses simple digital components (low cost).
•	Time: Can be implemented within the course duration.
•	Complexity: Moderate level suitable for students.
•	Resources: Easily available simulation tools.


5. Possible Solutions

Possible approaches include:
1.	Microcontroller-based voting system 
2.	FPGA-based system 
3.	Logic gate-based system (selected) 
The logic gate-based solution is chosen because:
•	It matches course requirements 
•	It is simpler and easier to simulate 
•	No programming required


6. Preliminary Design

The system is divided into blocks:
•	Input control block 
•	Mode selection block 
•	Candidate selection block 
•	Vote validation block 
•	Output display block 
Flow:
1.	User selects candidates 
2.	System checks validity 
3.	The vote is recorded 
4.	Output is updated


7. Design Description

The design consists of:
2x1 MUX for Mode Selection
If mode is 0, Voter Mode is ON; if mode is 1, Admin Mode is ON; voting stops in Admin Mode.

2x4 Decoder for the selection of Candidates
The Decoder selects the specific Candidate whose vote is recorded, while the other candidates remain unselected.

AND GATES implementation for Anti-repeat logic
Four 3-input AND GATES for each candidate that make sure the validation of the vote for a particular candidate, and prevent the circuit from repeating this.

SR LATCH for locking and unlocking candidates
SR LATCH is used to lock a candidate when he is selected and keep it locked until RESET.

Edge Detection
The vote button is used to vote for a selected candidate, and after that, a D flip-flop is used for edge detection so that the vote only counts once when the rising edge of the clock occurs.

Counters for counting the number of votes
12 D flip-flops are used, 3 for each candidate, for a 3-bit synchronous counting.

4x1 MUX for displaying the votes of selected candidates
Three 4x1 are used, the first 4x1 mux is for selecting the first bits for each candidate, the second for the second bits, and the third for the third bits for each candidate.
BCD to seven-segment
Four BCD to seven-segment (7448) is used to convert 3-bit counting into seven-segment for each Candidate.

Seven-Segment Display
Finally, four seven-segment displays are used to display all votes for each Candidate.

8. Software Simulation

The circuit was implemented in Logic Works 5 software using the .cct file.
Simulation verifies:
•	Correct vote selection 
•	No duplicate voting 
•	Proper switching between modes

	
9. Experimental Results

Results show:
•	Each vote is counted correctly 
•	Multiple votes are blocked 
•	Candidate selection works properly 
•	Output matches expected behavior

10. Performance Analysis

The system performs well in:
•	Accuracy 
•	Speed (instant output) 
•	Reliability 

Limitations:
•	Limited number of candidates
They can be increased using a 3x8 decoder, but I used a 2x4 decoder for simplicity
•	No memory storage for long-term data
As I used 3-bit counters, that’s why the machine counts from 0 to 7; if I use 4-bit counters, then the machine counts from 0 to 15. 


11. Future Scope

Future improvements:
•	Add more candidates 
•	Use memory for vote storage 
•	Implement biometric verification 
•	Convert into a microcontroller-based system


12. Social and Cultural Implications

Digital voting systems improve transparency and trust in elections. They reduce fraud and human error. However, proper security measures must be ensured to prevent misuse.


13. Conclusion

The Digital Voting Machine was successfully designed using digital logic components. The system ensures secure and accurate voting with one-person-one-vote functionality. The project demonstrates the practical application of multiplexers, decoders, and logic gates in real-world systems.


14. References
1.	Digital Logic Design – Morris Mano 
2.	Course Lecture Notes
Flowchart of Digital Voting Machine Project
Vote Button	Reset / Next Voter	Master Reset	Clock
↓	↓	↓	↓
Anti-repeat Logic
NOR 1 & NOR 2 gates	Mode Selector
Vote / display mode
↓	↓
SR Latch
Lock until reset	Enable (EN/) Logic
NOT + AND gate
↓
Candidate Selector
S1, S0 → routes vote to C1–C4
↓	↓	↓	↓
Counter C1
Q0–Q2 FFs	Counter C2
Q0–Q2 FFs	Counter C3
Q0–Q2 FFs	Counter C4
Q0–Q2 FFs
↓	↓	↓	↓
Display MUX Q0	Display MUX Q1	Display MUX Q2	Display MUX Q3
^ Mode Selector feeds all 4 MUX 
↓	↓	↓	↓
74_48 Decoder
BCD → 7-seg	74_48 Decoder
BCD → 7-seg	74_48 Decoder
BCD → 7-seg	74_48 Decoder
BCD → 7-seg
↓	↓	↓	↓
7-Seg Display
Candidate 1	7-Seg Display
Candidate 2	7-Seg Display
Candidate 3	7-Seg Display
Candidate 4


 

