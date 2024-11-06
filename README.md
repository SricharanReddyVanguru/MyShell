MyShell - A Custom Unix Shell in C
MyShell is a custom Unix-like command-line shell written in C. This shell replicates many core features of Bash, supporting common commands, pipelining, redirection, and process control. It’s designed to provide a lightweight, manageable shell environment that implements several built-in commands and handles background and foreground tasks.

Project Overview
MyShell was developed to understand and practice system-level programming concepts in C. It provides a minimal environment to execute standard shell commands, manage processes, handle input/output redirection, and more, using core system calls and techniques such as fork, exec, pipe, and dup.

Key Features
Built-in Commands: MyShell includes several custom implementations of essential shell commands, such as cd, pwd, ls, echo, and more.
Process Management: The shell supports running processes in the foreground and background. Users can control processes with commands like fg, bg, jobs, and kill, making it easier to manage running tasks.
Piping and Redirection: MyShell implements piping (|) to channel output from one command as input to another and supports input/output redirection using >, >>, and <.
Command Chaining: Using logical operators (&& and ||), users can create complex command sequences with conditional execution based on previous command success or failure.
Prompt Customization: The prompt displays username, hostname, and the current working directory, with support for a ~ shorthand to represent the home directory.
Signal Handling: MyShell handles essential Unix signals (e.g., SIGINT for interrupting a process with Ctrl+C and SIGTSTP for stopping with Ctrl+Z).
How to Compile and Run
Compile:

bash
Copy code
make
This command compiles all source files and links them into a single executable.

Execute:

bash
Copy code
./shell
This will start MyShell, displaying a prompt where you can enter commands.

Built-In Commands
MyShell implements custom versions of these commands:

cd: Changes the current directory.
pwd: Prints the current working directory.
ls: Lists files and directories.
echo: Prints a message to the standard output.
pinfo: Displays information about a process.
history: Shows recently executed commands.
nightswatch: A utility to monitor interrupts or new processes.
jobs: Lists all background processes.
fg / bg: Moves a background process to the foreground or resumes a stopped process.
overkill: Terminates all background processes.
quit: Exits the shell.
Shell Programming Concepts Used
System Calls:

fork(): Used to create new processes.
execvp(): Executes commands by replacing the current process image.
waitpid(): Manages process synchronization.
pipe(), dup(), and dup2(): Used for inter-process communication and I/O redirection.
Signal Handling:

Custom handlers for signals like SIGINT and SIGTSTP enable the shell to manage interruptions and job control.
Input Parsing and Command Execution:

Tokenization and parsing functions break down user input for individual command processing.
Chaining logic with logical operators allows for conditional command execution.
Process and Job Control:

The shell supports both background (&) and foreground process execution, allowing users to manage jobs efficiently.
Job tracking with process IDs (PIDs) and job IDs to manage multiple active processes.
File I/O Redirection:

Redirect standard input, output, and error to files or other commands using the dup and dup2 system calls.
Example Usages
bash
Copy code
# Basic commands
ls -l
cd /home/user
echo "Hello World"

# Running processes in the background
sleep 30 &

# Using pipes and redirection
ls | grep "pattern" > output.txt
cat < input.txt | sort > sorted_output.txt

# Command chaining
mkdir test_dir && cd test_dir || echo "Failed to create or enter directory"

# Process management
jobs           # List background jobs
fg %1          # Move job 1 to the foreground
bg %2          # Resume job 2 in the background
overkill       # Terminate all background processes
Future Enhancements
Command Recall: Implement arrow keys to navigate through the command history.
Auto-completion: Enable tab-based command and file name auto-completion.
Environment Variables: Add support for environment variable manipulation.
Aliases: Allow custom command aliases.