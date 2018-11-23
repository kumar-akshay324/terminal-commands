## Terminal Commands
A curated list of terminal commands for Ubuntu/Linux. 

## Process Handling

* Kill a process 

	* Using process name

		`sudo pkill -9 <process_name>`

	* Using process ID

		`ps aux | grep <process_name>`		// Get process ID
		`sudo pkill -9 <PID>`				// Kill process using ID

	* Using parent process (When sometimes killing the process using PID leaves it defunct)

		`ps -o ppid=<PID>`					// Get parent PID
		`sudo pkill -9 <PPID>`				// Kill process using ID

	* Sometimes, *Ctrl + Z* is used to kill programs when *Ctrl + C* fails. However, *Ctrl + Z* does NOT kill the program but merely sends it to the background of the current terminal. To kill such processes and any other process running in a particular window of the terminal.

		`sudo kill `jobs -p``

## Handle terminal outputs

* Several occasions of compiling a code leaves behind a lot of terminal outputs - errors, warnings and other information. If you’re fed up of scrolling through the terminal to notice each of them, use piping and redirection operators to send the output to files.
* Example `./executable > ~/tmp/output_stored.txt`

![alt text](https://github.com/kumar-akshay324/terminal-commands/blob/master/images/terminal_ouput.png "Terminal command suffixes to redirect screen output")

## Debug hardware issues

* Use these commands to discover different hardwares 

	* `lshw`					// hardware
	* `lspci`					// PCI devices
	* `lsusb`					// USB buses, 							
	* `lsblk`					// blocked devices and 
	* `lsmod`					// hardware modules plugged into the system

## Git command-line interface - Linux Terminal

* Add files to commit

	`git add .`					// Select all files to commit
	`git add <file_name>` 		// Select Particular file to commit
	`git add --all `			// Select Deletions to commit

* Commit files 
	`git commit -m <"commit message">`

* Manage files between local and remote repository

	*	Get updates from remote repository to local git (Only stored changes, NOT merged into local files)
	`git fetch <branch_name>` 		// Branch specific changes to see from remote
	`git fetch` 					// All remote changes from all branches

	*	Push all changes locally committed changes to remote repository
	`git push origin <branch name>`

	*	Before pushing to remote, pull to local repository (A pull is basically a fetch + merge )  
	`git pull origin <branch_name>`

	*	Merge changes from a remote/local branch to local branch
	`git merge <branch_name>`		// If conflicts come up, resolve manually in local files and commit to remote 

* Branch Commands

	`git checkout <branch_name>`	// Switch to the specified branch
	`git checkout <commit_id>`		// Switch to a particular commit ID on the current branch
	`git checkout -b <new_branch_name> <base_branch_name>`

* Discard/Archive edits

	`git stash`						// Remove all new unwanted edits
	`git stash list`				// Obtain the list of stashed or archived changes
	`git stash save "<message_to_save_edit>"`
	`git stash apply`				// Apply last stashed set of changes to edits
	`git stash apply --index`		// Apply particular stashed changes from the list 

* General Commands

	`git init .` 					// Initialize git in a local folder
	`git clone remote_git_url`		// Clone a remote repository to a local location
	`git status`					// Check status of repository to see tracked/committed/unco
	`git diff`						// Check the difference and edits in new uncommitted files
	`git branch`					// Check the branches available
	`git tag`						// Check the tags available
	`git reset --hard`				// Reset the all changes and get to master branch
	`git log`						// See history for commits, messages and authors
	`git blame <file_name>`			// List the changes, date and authors for the file

* Configure user credentials
	
	*	Add username for remote git service account
	`git config --global user.name "<github/bitbucket user_name>"`
	
	*	Add email ID for remote git service account
	`git config --global user.email "<github/bitbucket user_mail_id>"`

	*	Connect a local repository to remote git service URL
	`git remote add origin "<github/bitbucket repository URL>"`

	*	Set the origin/remote git service URL to current local repository
	`git set-url remote origin "<github/bitbucket repository URL>"`

## Miscellaneous terminal commands
	
* Terminal content handling
	`clear`						// Scroll the terminal to clear view - This does NOT erase the terminal history
	`reset`						// Erase the terminal history and present a clear screen
	`tree`						// Show the hierachy of existing files in the current folder
	`locate <file_name>`		// Search the folder location of a file
	`pwd`						// Print the current working directory
	`history`					// Get the history of all terminal commands in the window
	`man <terminal_command>`	//

## File Management via Terminal 

* Handling Directories
	
	`mkdir -p <path_to_file/file_name>`			// Create a folder in a specific location
	`mv  <file_to_move> <destination>`			// Move a file to a new location
	`rm <path_to_directory/file_to_remove>`		// Delete the particular folder/file
	`rm -rf <path_to_directory_to_remove>`		// Delete with *-r* flag for recursive and *-f* for forced (*-rf* Combined both)		

* Modifying new files

	`cat > file_name`							// Creates a new file in the particular location
	`cat file_name`								// Displays the content of the file in the terminal
	`cat file_1 file_2 > file_3`				// Joins two files (file_1, file_2) and stores the output in a new file file_3
	`less file_name`							// Displays the contents of the file with more [options] (https://en.wikipedia.org/wiki/Less_(Unix)) 

* Viewing the directory contents
	
	`ls`										// List files and directories in the current working directory
	`ls -a`										// List files including the hidden files
	`ls -R`										// List all the files in the sub directories
	`ls -al`									// List files with all permissions, size, owner, date of modification etc.

## Network Management via Terminal

* `ifconfig`									// Show network information like IP address, HW address and other parameters
* `iwconfig`									// Show wireless information
* `iwlist scan`									// Scan for all wireless networks / Run with `sudo`, ideally
* `sudo /etc/init.d/networking restart`			// Restart the network configuration - All wireless and wired connections

## System Service Management

* `start | stop <service>`						// Start or Stop the particular system service
* `status <service>`							// Check the status of the running service, whether active or not
* `etc/init.d/service start | stop | retsart`	// Toggle a system service
* `runlevel`									// Get current run level