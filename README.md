# 377-final-project

## Code Description
<sub>mainly focusing on exec_command() function</sub>
### Piping commands
The first thing that was implemented was the piping commands (|). I declared a variable to keep track of the index of the pipe operator, if it existed. If it did exist (index != -1), then I called pipe and fork and handled each process, duplicating the proper file descriptor. The child process executed the first set of commands and the parent the second. 

### Redirect STDOUT
Next, I handeled the redirection of standard output (>). Similar to pipe, I kept track of the index of the redirection operator. If the index was not -1, meaning there was a redirection, I opened the argument file that would take in the output of the first set of commands and then exectued the command.

### Builtin commands
If there was no pipe or redirection, I checked if it was a command I needed to handle separately. I created a seperate function called cmd_handler(), which exec_command() calls, to handle functions outside of the regular Linux shell. This function handles 4 different commands: "pwd", "cd", "help", and "tim".
* pwd: This bash command prints out the current working directory. I did this by using the function getcwd(), which takes in a buffer and the size of a buffer and prints out the path to the buffer. 
* cd: This bash command changes the current working directory to the specified location. I did this by using the function chdir(), which changes the current working directory to the input. 
* help: This bash command provides informatiobn on the shell's builtin commands. I call the function openHelp() which simply puts a string detailing the shell's functionality and what all can be done. 
* tim: This command is a command I personally implemented that prints out "Tim is the best!" in cool ascii art. Just a silly command!

### Linux shell general commands
If there was no pipe, redirection, and it was not a command I needed to handle seperately, I used fork and execvp to normally execute the command using the argument given. 

## Video Presentation

## Resources Used
https://www.gnu.org/software/bash/manual/html_node/Bash-Builtins.html
https://www.educative.io/blog/bash-shell-command-cheat-sheet
https://www.geeksforgeeks.org/making-linux-shell-c/
https://stackoverflow.com/questions/26788603/simple-shell-with-pipe-function
https://patorjk.com/software/taag/#p=display&f=Big&t=Tim%20is%20the%20best!
https://man7.org/linux/man-pages/man2/getcwd.2.html
https://stackoverflow.com/questions/11515399/implementing-shell-in-c-and-need-help-handling-input-output-redirection
https://www.geeksforgeeks.org/pipe-system-call/
