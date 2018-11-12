## Terminal Commands
A curated list of terminal commands for Ubuntu/Linux. 

# Process Handling


* Kill a process 

	* Using process name

		`sudo pkill -9 <process_name>`
	* Using process ID

		`ps aux | grep <process_name>`		// Get process ID
		`sudo pkill -9 <PID>`				// Kill process using ID
	* Using parent process (When sometimes killing the process using PID leaves it defunct)

		`ps -o ppid=<PID>`					// Get parent PID
		`sudo pkill -9 <PPID>`				// Kill process using ID

# Handle terminal outputs

* Several occasions of compiling a code leaves behind a lot of terminal outputs - errors, warnings and other information. If you’re fed up of scrolling through the terminal to notice each of them, use piping and redirection operators to send the output to files.
* Example `./executable > ~/tmp/output_stored.txt`

![alt text](https://github.com/kumar-akshay324/terminal-commands/raw/master/images/terminal_output.png "Terminal command suffixes to redirect screen output")

# Debug hardware issues

* Use these commands to discover different hardwares 

	* `lshw`			// hardware
	* `lspci`			// PCI devices
	* `lsusb`			// USB buses, 							
	* `lsblk`			// blocked devices and 
	* `lsmod`			// hardware modules plugged into the system
