# SSH_Bruteforce
There are two approaches for the same problem

The sshbrute.py uses a simple SSH bruteforce attack for a specific targert that the user inputs.

The program tries to find a correct password from a given file.

The passwords.txt file is an example file and is not recomended for actual use.

The sshbrutethreaded.py uses the same logic and also makes use of threads for a faster solution to the attack.


This Python script is a simple tool for attempting to perform SSH password authentication attacks on a target host. Here's a breakdown of its functionality:

1. **Imported Modules:**
   - `paramiko`: A library for SSH connections.
   - `sys`: Provides access to some variables used or maintained by the Python interpreter.
   - `os`: Provides a way to interact with the operating system, here, it's used to check if a file exists.
   - `socket`: Provides low-level network programming.
   - `termcolor`: Adds ANSI color to the terminal text.

2. **Function Definition: `ssh_connect`**
   - Parameters:
     - `password`: The password to be tested during the SSH connection attempt.
     - `code`: A status code indicating the result of the connection attempt.
   - Functionality:
     - Initializes a Paramiko SSHClient.
     - Sets the host key policy to automatically add unknown hosts.
     - Attempts to connect to the SSH server using the provided host, username, and password.
     - Handles exceptions for authentication failures (`paramiko.AuthenticationException`) and socket errors (`socket.error`).
     - Closes the SSH connection and returns the status code.

3. **User Input:**
   - Takes user input for the target host address (`host`), SSH username (`username`), and a file containing passwords (`input_file`).

4. **File Existence Check:**
   - Checks if the specified password file exists. If not, it prints an error message and exits the script.

5. **Password Testing Loop:**
   - Opens the specified password file (`input_file`) in read mode.
   - Iterates through each line in the file, treating each line as a password.
   - Calls the `ssh_connect` function with the current password.
   - Prints messages based on the result of the connection attempt:
     - If successful (code 0), it prints the found password and exits.
     - If authentication fails (code 1), it prints an incorrect login message.
     - If a socket error occurs (code 2), it prints a connection error message and exits.
   - Catches and prints any other exceptions that might occur during the connection attempt.

6. **Note:**
   - The script uses ANSI color codes for better visualization of the output in the terminal, making successful attempts green, incorrect logins in regular text, and connection errors in red.

7. **Potential Improvement:**
   - This script is a basic example and is meant for educational purposes only. In real-world scenarios, attempting unauthorized access to systems is illegal and unethical. Always ensure that you have explicit permission before attempting any form of security testing or penetration testing.
