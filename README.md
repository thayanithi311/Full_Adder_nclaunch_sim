# EXP1: 4 Bit Adder functionality verification

**Aim:**

To write a verilog code for 4bit adder and verify the functionality using Test bench.<br>

&emsp;&emsp;Write Verilog Code<br>

&emsp;&emsp;Verify the Functionality using Test-bench.<br>

**Tool Required:**

&emsp;&emsp;Functional Simulation: nclaunch Simulator (nclaunch) <br>

**4-bit Adder Design:**

&emsp;&emsp;To construct a 4-bit adder, need to chain together four 1-bit full adders. Each full adder computes the sum and carry for one bit of the two numbers. The carry-out from one adder feeds into the carry-in of the next adder in the sequence. This process adds the two 4-bit numbers bit by bit, with the carry propagating through each stage, resulting in a final sum and carry-out at the end.<br>

&emsp;&emsp;To design a 1-bit full adder, the first step is to create a truth table that represents all possible combinations of the inputs (A, B, and CIN) and the corresponding outputs (Sum(S) and COUT).<br>

![image](https://github.com/user-attachments/assets/716a26b6-a449-42e0-9e2d-cdbaa4b291b9)

Here’s the truth table for a 1-bit full adder:

![tt](https://github.com/user-attachments/assets/0b3ab24f-1d7e-4a01-80ce-5e7406f4082b)

**Fig 1 : Diagram and truth table of full adder**

**Logic Expressions:**

1.	Sum (S):
   
&emsp;&emsp;S=A⊕B⊕CIN

&emsp;&emsp;Where ⊕ represents XOR.

3.	Carry out (COUT):
   
&emsp;&emsp;COUT=(A&B) | (CIN&(A^B))

![image](https://github.com/user-attachments/assets/7d6fa554-2614-4f19-aa68-65c9e6153caa)

**Fig 2:Diagram of 4 Bit Adder**

**Creating Source Codes**

&emsp;&emsp;In the Terminal, type gedit <filename>.v (ex: gedit 4bitadder.v). <br>

&emsp;&emsp;A Blank Document opens up into which the following source code can be typed down. <br>

&emsp;&emsp;Note : File name should be with HDL Extension<br>

**a) Verify the Functionality**

&emsp;&emsp;Three Codes shall be written for implementation of 4-bit Adder as follows, <br>

&emsp;&emsp;&emsp;&emsp;fa.v → Single Bit 3-Input Full Adder [Sub-Module / Function] <br>

&emsp;&emsp;&emsp;&emsp;fa_4bit.v → Top Module for Adding 4-bit Inputs. <br>

&emsp;&emsp;&emsp;&emsp;fa_4bit_test.v → Test bench <br>

*/Program to design 4 bit adder by instantiating 1 bit Full adder.also add test bench program */ Developed by: Register Number*/

**Functional Simulation:**

&emsp;&emsp;Invoke the cadence environment by type the below commands <br>

&emsp;&emsp;tcsh (Invokes C-Shell) <br>

&emsp;&emsp;source /cadence/install/cshrc (mention the path of the tools) <br>

&emsp;&emsp;```(The path of cshrc could vary depending on the installation destination)<br>```
      
&emsp;&emsp;After this you can see the window like below <br>

![Screenshot 2024-09-23 111003](https://github.com/user-attachments/assets/92074978-05f2-481a-bbfb-6c35a3dc37e3)


**Fig 3:Invoke the Cadence Environment**

&emsp;&emsp;To Launch Simulation tool <br>

&emsp;&emsp;&emsp;&emsp;linux:/> nclaunch -new& // “-new” option is used for invoking NCVERILOG for the first time for any design <br>

&emsp;&emsp;&emsp;&emsp;or<br>

&emsp;&emsp;&emsp;&emsp;linux:/> nclaunch& // On subsequent calls to NCVERILOG <br>

&emsp;&emsp;It will invoke the nclaunch window for functional simulation we can compile,elaborate and simulate it using Multiple Step .<br>



**Fig 4:Setting Multi-step simulation**

&emsp;&emsp;Select Multiple Step and then select “Create cds.lib File” .<br>

&emsp;&emsp;Click the cds.lib file and save the file by clicking on Save option <br>



**Fig 5:cds.lib file Creation**

&emsp;&emsp;Save cds.lib file and select the correct option for cds.lib file format based on the HDL Language and Libraries used. <br>

&emsp;&emsp;Select “Don’t include any libraries (verilog design)” from “New cds.lib file” and click on “OK” as in below figure .<br>

&emsp;&emsp;&emsp;&emsp;We are simulating verilog design without using any libraries <br>

&emsp;&emsp;&emsp;&emsp;A Click “OK” in the “nclaunch: Open Design Directory” window as shown in below figure <br>

![image](https://github.com/user-attachments/assets/781b297a-11e9-4140-89c5-ee3b0d15bbd4)

**Fig 6: Selection of Don’t include any libraries**

&emsp;&emsp;A ‘NCLaunch window’ appears as shown in figure below <br>

&emsp;&emsp;Left side you can see the HDL files. Right side of the window has worklib and snapshots directories listed. <br>

&emsp;&emsp;Worklib is the directory where all the compiled codes are stored while Snapshot will have output of elaboration which in turn goes for simulation .<br>

&emsp;&emsp;To perform the function simulation, the following three steps are involved Compilation, Elaboration and Simulation. <br>

![Screenshot 2024-09-23 111159](https://github.com/user-attachments/assets/dc000754-b2e3-4f89-8509-7f8856bdc429)



**Fig 7: Nclaunch Window**

**Step 1: Compilation:– Process to check the correct Verilog language syntax and usage**

&emsp;&emsp;Inputs: Supplied are Verilog design and test bench codes <br>

&emsp;&emsp;Outputs: Compiled database created in mapped library if successful, generates report else error reported in log file <br>

**Steps for compilation:**

&emsp;&emsp;1. Create work/library directory (most of the latest simulation tools creates automatically) <br>
&emsp;&emsp;2. Map the work to library created (most of the latest simulation tools creates automatically) <br>
&emsp;&emsp;3. Run the compile command with compile options <br>
&emsp;&emsp;i.e Cadence IES command for compile: ncverilog +access+rwc -compile fa.v<br>

&emsp;&emsp;Left side select the file and in Tools : launch verilog compiler with current selection will get enable. Click it to compile the code <br>

&emsp;&emsp;Worklib is the directory where all the compiled codes are stored while Snapshot will have output of elaboration which in turn goes for simulation<br>

![Screenshot 2024-09-23 111159](https://github.com/user-attachments/assets/5b942729-5746-4906-81ef-510f4af8fae0)


**Fig 8: Compiled database in worklib**

&emsp;&emsp;After compilation it will come under worklib you can see in right side window<br>

&emsp;&emsp;Select the test bench and compile it. It will come under worklib. Under Worklib you can see the module and test-bench. <br>

&emsp;&emsp;The cds.lib file is an ASCII text file. It defines which libraries are accessible and where they are located. It contains statements that map logical library names to their physical directory paths. For this Design, you will define a library called “worklib”<br>

**Step 2: Elaboration:– To check the port connections in hierarchical design**

&emsp;&emsp;Inputs: Top level design / test bench Verilog codes <br>

&emsp;&emsp;Outputs: Elaborate database updated in mapped library if successful, generates report else error reported in log file <br>

&emsp;&emsp;Steps for elaboration – Run the elaboration command with elaborate options <br>

&emsp;&emsp;&emsp;&emsp;1.	It builds the module hierarchy <br>
&emsp;&emsp;&emsp;&emsp;2.	Binds modules to module instances <br>
&emsp;&emsp;&emsp;&emsp;3.	Computes parameter values <br>
&emsp;&emsp;&emsp;&emsp;4.	Checks for hierarchical names conflicts <br>
&emsp;&emsp;&emsp;&emsp;5.	It also establishes net connectivity and prepares all of this for simulation<br>
   
&emsp;&emsp;After elaboration the file will come under snapshot. Select the test bench and elaborate it.<br>


![Screenshot 2024-09-23 111159](https://github.com/user-attachments/assets/cf2a39de-395f-45fe-9b16-985a4e906df5)


**Fig 9: Elaboration Launch Option**

**Step 3: Simulation: – Simulate with the given test vectors over a period of time to observe the output behaviour.**

&emsp;&emsp;Inputs: Compiled and Elaborated top level module name <br>

&emsp;&emsp;Outputs: Simulation log file, waveforms for debugging <br>

&emsp;&emsp;Simulation allow to dump design and test bench signals into a waveform <br>

&emsp;&emsp;Steps for simulation – Run the simulation command with simulator options<br>

![Screenshot 2024-09-23 111215](https://github.com/user-attachments/assets/22648133-4451-4e5d-90bd-85ab197f3427)


**Fig 10: Design Browser window for simulation**

![Screenshot 2024-09-23 111259](https://github.com/user-attachments/assets/bae47748-9949-42d6-bda4-e4bcf403dd5a)

**Fig 11: Launching Simulation Waveform WindowSimulation Waveform Window**

![Screenshot 2024-09-23 111259](https://github.com/user-attachments/assets/63fdec84-883c-4018-b6db-c9b19f434f39)


**Fig 12: Simulation Waveform Window**















