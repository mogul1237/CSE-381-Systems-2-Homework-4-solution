# CSE-381-Systems-2-Homework-4-solution

Download Here: [CSE-381: Systems 2 Homework #4 solution](https://jarviscodinghub.com/assignment/cse-381-systems-2-homework-4-solution/)

For Custom/Original Work email jarviscodinghub@gmail.com/whatsapp +1(541)423-7793

Develop a custom Linux shell
Background
Operating Systems essentially provide system calls to run programs, but an OS does not start
running programs by itself. This task is delegated to another program, called a “shell”. The shell
(in our case we are using bash shell) accepts inputs from the user and based on the user-input
executes different commands. Note that shells can be graphical (one desktop on Linux is called
Gnome shell) and permit users to double-click on an icon to indicate the program to run.
Homework requirements
This homework requires developing a textual shell program analogous to bash used in Linux.
Note that the shell you will be developing will be rather simple when compared to bash, but
will help you obtain a good understanding of how a shell works. Your shell must operate in the
following manner:
Repeatedly prompt (via a simple “> “) and obtain a line of input (via std::getline) from
the user and process each line of input in the following order:
• If the line is empty or the line begins with a pound (#) sign, ignore those lines.
• The 1st word in the line is assumed to be a command (case sensitive) and must be
processed as:
1. If the command is exit your shell must terminate
2. If the command is SERIAL then the 2nd word is name of a file that contains the
actual commands to be executed one at a time. The shell waits for each command
to finish.
3. If the command is PARALLEL then the 2nd word is name of a file that contains the
actual commands to be executed. In this case, all the commands are first exec’d.
Then wait for all the processes to finish in the same order they were listed.
4. If the 1st word is not one of the above 3, then it is assumed to be the name of the
program to be executed and rest of the words on the line are interpreted as a
command-line arguments for the program.
Note: For every command run (including SERIAL and PARALLEL runs), the shell must print
the command and command line arguments. Once the command has finished, the shell must print
the exit code. See sample outputs for wording and spacing.
Tips & suggestions
• This homework deals with concepts from Exam #1. In prior semesters it was assigned before
Exam #1. However, this semester we are going a bit slow and this program is coming after
Exam #1. Nevertheless, this homework helps solidify concepts from the course. Importantly,
it is a good program to showcase on Git hub and build your resume.
• A lot of the code you need is already in lecture slides. So ensure you review some of the
material on string processing, vector, fork, and exec before starting on the program.
• When calling exec don’t forget the nullptr at the end of command-line arguments
• Get base case working first. The string processing is trivial (almost all the code in slides)
with std::quoted. Do not overcomplicate the string processing part.
DUE DATE: Tue, October 16 2018 Before 11:59 PM (EST)
Page 3 of 4
• If you code the base case method to use generic I/O streams then processing commands from
files becomes straightforward.
• Use a std::vector to hold PIDs of child processes so that you can call waitpid on each
one when running them in parallel.
Sample input and outputs
In the sample outputs below, the following convention is used:
• Text in bold are inputs (logically) typed-in by the user (↵ is for pressing enter key)
• Text in blue are additional outputs printed by your program
• Other text are outputs from various commands exec’d by your program
Base case (10 points) > # Lines starting with pound signs are to be ignored.↵
> echo “hello, world!” ↵
Running: echo hello, world!
hello, world!
Exit code: 0
> ↵
> head -2 /proc/cpuinfo↵
Running: head -2 /proc/cpuinfo
processor : 0
vendor_id : GenuineIntel
Exit code: 0
> ↵
> # A regular sleep test. ↵
> sleep 1↵
Running: sleep 1
Exit code: 0
> ↵
> # Finally exit out↵
> exit↵
SERIAL test (7 points) > echo “serial test take about 5 seconds”↵
Running: echo serial test take about 5 seconds
serial test take about 5 seconds
Exit code: 0
> SERIAL simple.sh↵
Running: sleep 1
Exit code: 0
Running: sleep 1s
Exit code: 0
Running: sleep 1.01
Exit code: 0
Running: sleep 0.99
Exit code: 0
Running: sleep 1s
Exit code: 0
> exit↵
PARALLEL test (8 points)
> # echo “parallel test take about 1 second”↵
> PARALLEL simple.sh↵
Running: sleep 1
Running: sleep 1.01
Running: sleep 1s
Running: sleep 0.99
DUE DATE: Tue, October 16 2018 Before 11:59 PM (EST)
Page 4 of 4
Running: sleep 1s
Exit code: 0
Exit code: 0
Exit code: 0
Exit code: 0
Exit code: 0
> exit↵
Organization and structure verification
In order to earn the full 5 points in this category, the program should strive to reuse code as much
as possible. Specifically, processing lines from files (in SERIAL or PARALLEL command)
should reuse code from the method used for processing individual commands. This kind of code
reuse will be an important expectation in your future jobs.
Submit to Canvas
This homework assignment must be turned-in electronically via CODE Canvas plug-in. Ensure
all of your program(s) compile without any warnings or style violations and operate correctly.
Once you have tested your implementation, upload the following onto Canvas:
• The 1 C++ source file for this part of the homework, with the naming convention
MUID_hw4.cpp, where MUID is your Miami University unique ID.
Upload each file associated with homework (or lab exercises) individually to Canvas. Do not
upload archive file formats such as zip/tar/gz/7zip/rar etc.
