# A simple scheduler simulator for Operating Systems 
Platform: Linux
Language: C/C++

## Introduction
A CPU scheduler determines an order for the execution of its scheduled processes; it decides which
process will run according to a certain data structure that keeps track of the processes in the system and
their status.

A process after creation has one of the three states: Running, Ready, Blocked (doing I/O , using other
resources than CPU or waiting on unavailable resource).

A bad scheduler will make a very bad Operating System, so your scheduler should be as much
optimized as possible in terms of memory and time usage.

## System Description
Consider a Computer with
1-CPU and infinite memory, the scheduler with its complementary components as the following

### Part 1: Process generator  (Objective: For simulation & IPC)
#### Code file: processGenerator.cpp
Process generator: responsible for
● Reading the input files (check Part 5)
● Ask the user about the chosen scheduling Algorithm and its parameters if exists.
● Initiate and create Scheduler and Clock processes.
● Creating a data structure for process and provide it with its parameters
● Send the information to the scheduler at the appropriate time (only when a process arrives) so
that it will be put it in its turn.
● At the end it Clear IPC Resources.

### Part 2: Clock  (Objective: For simulation & IPC)
#### Code file: clk.cpp
The clock module is used to emulate a integer time clock
headers.h contains clk functions. 
It should be included anywhere the clock functions are used.
To get time call, use: 
  <br>`getClk();`  
  
### Part 3 : Scheduler (Objective: OS Design, IPC)
#### Code file: scheduler.cpp
The scheduler is the core of your work, it should keep track of the processes and their states
And it decides – based on the used algorithm - which process will run & for how long.

The scheduler consists of mainly three Algorithms:
1. non-preemptive HPF
2. Shortest Remaining time Next
3. Round Robin

The scheduling algorithm only works on the processes in the ready queue. (Process that already
arrived).

The Scheduler should be able to
● Start a new process according to the scheduling algorithm.(Fork it and give its parameters)
● Switch between two processes according to the scheduling algorithm. (Stop the old process and
save its state and start/resume another one)
● At anytime, it should have a process control Block that keeps track of the state of the processes
in the system (running/waiting/execution time/ remaining time/ waiting time/ ...etc)
● If the scheduler is notified that a process finished, it delete its data.
○ When a process finishes it should notify the scheduler on termination, the scheduler
DOESN’T terminate the process.

For each algorithm you should report:
● CPU utilization.
● average weighted turnaround time.
● average waiting time.
● standard deviation for average weighted turnaround time.

The Scheduler Generates two files: (check Part 5)
● Scheduler.log
● Scheduler.perf

### Part 4 : process (Objectives: simulation, IPC)
#### Code file: process.cpp
The process should act as if runs in the execution time, the process communicate with clock functions.

### Part 5 : Input / output (Objectives: simulation, evaluation OS Design)
#### Input:
![input sample](https://raw.githubusercontent.com/MichaelKMalak/OS-Scheduler/blob/master/sample/input.PNG)
#### Output:
![first output sample](https://raw.githubusercontent.com/MichaelKMalak/OS-Scheduler/blob/master/sample/output_1.PNG)
![second output sample](https://raw.githubusercontent.com/MichaelKMalak/OS-Scheduler/blob/master/sample/output_2.PNG)

## How to use?
### To compile the project 
write on terminal
<br>`make`

### To run the project 
write on terminal
<br>`make run`

### Note
If you added a file to your project add it to the build section in the Makefile. Always start the line with a tab in Makefile, it is its syntax