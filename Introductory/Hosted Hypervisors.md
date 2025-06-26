<p align="center">
  <img src="https://tryhackme-images.s3.amazonaws.com/room-icons/66264cef7bba67a6bbbe7179-1725231171975" alt="Room Icon" width="200"/>
</p>

# Hosted Hypervisors
Created by <a href="https://tryhackme.com/p/tryhackme">tryhackme</a>, <a href="https://tryhackme.com/p/rePl4stic">rePl4stic</a>

## Task 1: Introduction
- Hosted Hypervisors are also known as Type 2 hypervisors.
- Operate on top of existing OS (indirectly communicate with underlying hardware).
- Manage virtual machines.

<br>

## Task 2: Environment and Setup
- Can use RDP to access the VM for this room.
  - Syntax: ```xfreerdp3 /u:(username) /p:(password) /v:(Machine IP) /dynamic-resolution``` 
- Username: Administrator
- Password: Hypervisors123

<br>

## Task 3: Networking & Memory Investigations
- Can detect if VirtualBox or VMware is installed on machine if you look in **Network Adapters**.
- ```ipconfig``` or PowerShell using command ```Get-NetAdapter``` works too.
- VirtualBox uses MAC addresses that start with ```08:00:27``` and ```0A-00-27```.
- VMware MAC addresses start with ```00:50:56```.
- We can use memory dump to know if hypervisor is present.
- Output of the plugin ```windows.pstree``` (lists processes in a tree-based format based on process parent ID) can reveal hypervisor's presence.
  - ```python vol.py -f ..\memdump.mem windows.pstree```
  - VMware - ```vmware.exe```, VirtualBox - ```VBoxSVC.exe```
- ```windows.netstat``` alows to verify if the communication comes from ```vmnat.exe``` (VMware) or ```VirtualBoxVM.exe``` (VirtualBox).
  - ```python vol.py -f ..\memdump.mem windows.netstat```
- To execute the above Python commands, you must navigate to the appropriate directory.
  - In the context of this room, you must be at: ```C:\Users\Administrator\Desktop\Volatility3```

<br>

#### Q1: What is the PID of the process vmware.exe on the memory dump: memdump.mem?
<pre>8096</pre>
You can find this in the room's VM. In command line, navigate to ```C:\Users\Administrator\Desktop\Volatility3```. Enter the command ```python vol.py -f ..\memdump.mem windows.pstree``` to list the processes and their IDs. Look for the process ID associated with ```vmware.exe```. You can use the ```>``` operator to move the output into a text file for easy searchability.
<br>

#### Q2: What is the name of VirtualBox service process in Windows?
<pre>VBoxSVC.exe</pre>

<br>

## Task 4: VirtualBox Investigations
### VBoxManage
- Located in ```C:\Program Files\Oracle\VirtualBox```
- Can find an executable called ```VBoxManage.exe```
- Start VM with a command: ```Vboxmanage.exe startvm {name of vm}```
- Enable debug logs: ```Vboxmanage.exe debugvm {name of vm} log --all```
### VirtualBox Logs
- General information about hypervisor can be found in: ```C:\Users\{username}\.VirtualBox```
- Files:
  - **VirtualBox.xml**: Configuration file. Can get useful info like interface IP, virtual interfaces, uid, log locations, etc.
  - **selectorwindow.log**: Information about VirtualBox process (details used to install/start).
  - **VboxSVC**: Saves info regarding start/stop use of VirtualBox and saves/deletes components.
  - **Vbox.log**: Contains OS information, architecture, and installation dates. VM plugins and drivers.
  - **VBoxHardening.log**: Memory management of hypervisor. Security-related crashes.
### VirtualBox Memory Dump
- Can create a memory dump of a VM in VirtualBox.
- First navigate to ```C:\Program Files\Oracle\VirtualBox``` and execute ```VBoxManage``` tool.
  -  ```VBoxManage.exe debugvm {name of the vm} dumpvmcore --filename={output file name}```
-  Next need to use Volatility2 (feature is not supported on Volatility3).
  - ```python vol.py -f {output file name} imagecopy -O {new output file name}```
  - Creates memory dump of machine to investigate internal memory.
- Can inspect snapshots on default directory.
  - ```C:\Users\user01\VirtualBox VMs\secretvm\Snapshots```
- Virtual disk used by VM can be found in VM directory - can be helpful.

<br>

#### Q1: Where is the VboxManage tool typically located?
<pre>C:\Program Files\Oracle\VirtualBox</pre>

<br>

#### Q2: Which file contains logs about the installation and the OS?
<pre>Vbox.log</pre>

<br>

## Task 5: Vmware Workstation Investigations
- Settings and configuration information can be found in ```C:\ProgramData\VMware\VMware Workstation```
  - **settings.ini**: Contains configuration settings for printers and disks.
  - **config.ini**: Specific configurations such as auto-update, access ports, and others.
  - **vmautostart.xml**: Contains configuration information on how virtual machines are supposed to start.
    - **vmxpath** filesystem path indicates where a VMware workstation's VM files are stored. 
- ```C:/ProgramData``` is hidden by default.
### VMware Workstation Logs
- ```C:\ProgramData\VMware\logs```
  - Name of log is something like: ```vmmsi.log_20240822_234016```
### VMware VM Memory Dump
- ```vmss2core``` - Allows us to take screenshot of VM and convert to a memory dump.
  - ```vmss2core -W {snampshot.vmss} {new name of dump.vmem}```

<br>

#### Q1: What file should you look at to determine which VMs have an autostart functionality?
<pre>vmautostart.xml</pre>

<br>

#### Q2: What file should you look at to determine which VMs have an autostart functionality?
<pre>C:\ProgramData\VMware\logs</pre>

<br>

## Task 6: Practical
The practical component involves using the volatility framework (as described in this room).

<br>

#### Q1: Investigate the VMware logs. Can you find the flag that starts with THM{}?
<pre>Investigate the VMware logs. Can you find the flag that starts with THM{}?</pre>
In the room's VM, navigate to ```C:\ProgramData\VMware\logs``` and open the log file. Ctrl+F and search for THM{ to find the flag.

<br>

#### Q2: Analyze the processes on the memory dump  C:\Users\Administrator\Desktop\exercise.mem on the room VM. What is the PID of the VBoxSVC.exe process?
<pre>6052</pre>
Use the command ```python vol.py -f ..\exercise.mem windows.pstree > {text_file}```. Replace {text_file}. It is recommended to write out the output to a text file. Once the scanning is complete, open the file and search for VBoxSVC.exe. You will find the process ID associated with the process.

<br>

#### Q3: Analyze the processes on the memory dump  C:\Users\Administrator\Desktop\exercise.mem on the room VM. What is the IP of the Virtual Network Adapter?
<pre>192.168.182.139</pre>
Use the command ```python vol.py -f ..\exercise.mem windows.netstat > {text_file}```. The local address indicates the IP address used by the virtual network adapter (Owner is VirtualBoxVM.exe).
