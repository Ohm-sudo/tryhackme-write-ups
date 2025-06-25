<p align="center">
  <img src="https://tryhackme-images.s3.amazonaws.com/room-icons/5f04259cf9bf5b57aed2c476-1718096949787" alt="Room Icon" width="200"/>
</p>

# Windows Command Line
Created by <a href="https://tryhackme.com/p/tryhackme">tryhackme</a>, <a href="https://tryhackme.com/p/strategos">strategos</a>

## Task 1: Introduction
- Advantages using a CLI:
  - Lower resource usage.
  - Automation.
  - Remote management.
- SSH syntax: ```ssh <username>@<MACHINE_IP>```
  - The credentials for this room:
    - Username: ```user```
    - Password: ```Tryhackme123!```

<br>

#### Q1: What is the default command line interpreter in the Windows environment?
<pre>cmd.exe</pre>
<br>

## Task 2: Basic System Information
- Can use the command, ```set``` to check your path from command line.
- ```ver``` is a command used to determine operating system version.
- ```systeminfo``` command lists various information about the system.
  - OS information.
  - System details.
  - Processor and memory.
- Can pipe the output using ```more``` if output too long (view page-by-page)
  - Try running ```driverquery``` and compare with running ```driverquery | more```.
- Other useful commands:
  - ```help```
  - ```cls``` - Clears command prompt screen.

<br>

#### Q1: What is the OS version of the Windows VM?
<pre>10.0.20348.2655</pre>
You can find this by entering the ```ver``` command.

<br>

#### Q2: What is the hostname of the Windows VM?
<pre>WINSRV2022-CORE</pre>
You can find this by entering the ```systeminfo``` command.

<br>

## Task 3: Network Troubleshooting
- Check network information using ```ipconfig``` command.
  - Can also use ```ipconfig /all``` for more information.
- Troubleshoot by using ```ping``` command to verify if target can be reached.
- ```tracert``` can also be used for troubleshooting to determine which routers has been passed by the packet towards the destination.
- ```nslookup``` looks up host/domain name and returns its IP.
  - Syntax: ```nslookup <host/domain> <name_server_IP>```
- ```netstat``` displays current network connections and listening ports.
  - If curious about options associated with netstat, enter ```netstat -h```
   - ```-a``` shows all established connections and listening ports.
   - ```-b``` shows program associated with each listening port and established connection.
   - ```-o``` reveals process ID (PID) associated with the connection.
   - ```-n``` uses numerical form for addresses and port numbers.
   - Can all be combined to execute ```netstat -abon``` command.

<br>

#### Q1: Which command can we use to look up the server’s physical address (MAC address)?
<pre>ipconfig /all</pre>
<br>

#### Q2: What is the name of the process listening on port 3389?
<pre>TermService</pre>
Use the command ```netstat -abon``` and scroll down until you can see the entry associated with port 3389 to find the answer.
<br>

#### Q3: What is the subnet mask?
<pre>255.255.0.0</pre>
Subnet mask can be found by entering ```ipconfig /all``` command.

<br>

## Task 4: File and Disk Management
- ```cd``` command to navigate between directories.
  - ```cd ..``` to go up one level. 
- ```dir``` view child directories.
  - ```dir /a``` - Displays hidden and system files.
  - ```dir /s``` - Displays files in current directory and all subdirectories.
- ```mkdir directory_name``` - creates a directory.
- ```rmdir directory_name``` - removes a directory.
- ```type``` - view text files.
- ```copy``` - copies files from one location to another.
  - i.e., ```copy test.txt test2.txt```
- ```move``` move files.
- ```del``` or ```erase``` - delete a file.
- Can use a wildcard (*) to refer to multiple files.
  - i.e., ```copy *.md C:\Markdown``` copies all files with extension ```md``` to ```C:\Markdown```.

<br>

#### Q1: What are the file’s contents in C:\Treasure\Hunt?
<pre>THM{CLI_POWER}</pre>
First cd to ```C:\Treasure\Hunt``` then enter ```dir /a``` to see files in current directory. Enter ```type flag.txt``` to read the contents of the text file containing the flag.

<br>

## Task 5: Task and Process Management
- ```tasklist``` - View list of running processes.
  - ```tasklist /?``` - Check all available filters; displays help page.
  - i.e., Search for tasks related to ```sshd.exe``` can be done using the command ```tasklist /FI "imagename eq sshd.exe"```
    - ```/FI``` used to set filter image name equals ```sshd.exe.
  - With known process ID (PID), terminate task using ```taskkill /PID target_pid```

<br>

#### Q1: What command would you use to find the running processes related to notepad.exe?
<pre>tasklist /FI "imagename eq notepad.exe"</pre>
<br>

#### Q2: What command can you use to kill the process with PID 1516?
<pre>taskkill /PID 1516</pre>
<br>

## Task 6: Conclusion
- ```chkdsk``` - Checks file system and disk volumes for errors and bad sectors.
- ```driverquery``` - Displays installed device drivers.
- ```sfc /scannow``` - Scan system files for corrupts and repairs them if possible.
- You can use ```/?``` after a command to get help on the usage of the command.

<br>

#### Q1: The command ```shutdown /s``` can shut down a system. What is the command you can use to restart a system?
<pre>shutdown /r</pre>
<br>

### Q2: What command can you use to abort a scheduled system shutdown?
<pre>shutdown /a</pre>
The answers to Q1 and Q2 can be found by entering ```shutdown /?``` command.
