<p align="center">
  <img src="https://tryhackme-images.s3.amazonaws.com/room-icons/5de96d9ca744773ea7ef8c00-1723540339114" alt="Room Icon" width="200"/>
</p>

# Hypervisor Internals
Created by <a href="https://tryhackme.com/p/tryhackme">tryhackme</a>, <a href="https://tryhackme.com/p/cmnatic">cmnatic</a>, <a href="https://tryhackme.com/p/MonAha">MonAha</a>

## Task 1: Introduction
- Virtualization is the concept of creating virtual environments within physical hardware.
  - Achieved by allocating computing resources to these environments.
- Benefits of virtualization:
  - Cost saving.
  - High availability.
  - Easier management.
  - Scalability.

<br>

## Task 2: Type of Hypervisors
### Type 1 (Bare metal)
- Direct access to system's physical hardware.
- Benefits:
  - Performance
  - Scalability
  - Sophistication
- Examples: Hyper-V, VMware ESXi.
- Form the backbone of cloud computing.
### Type 2 (Hosted)
- Run on top of an existing operating system.
- Like a program.
- Benefits:
  - Ease of use.
  - Free offerings.
  - Widely compatible.

<br>

#### Q1: What type of Hypervisors have direct access to bare metal?
<pre>type 1</pre>
<br>

#### Q2: What type of Hypervisors do not have access to bare metal but run inside and through another Operating System?
<pre>type 2</pre>
<br>

## Task 3: Hypervisor Landscape
### Hyper-V
- Microsoft's take on virtualization.
- Manages Windows OS - giving the illusion that it is a type 2 hypervisor.
### VirtualBox
- Popular due to being open-source, free, and cross-platform nature.
### VMware ESxi
- Member of VMware's vSphere suite.
- Popular for large-scale virtualization.
- Features:
  - Clustering: Installations on multiple machines can be connected to each other.
  - Automation: Automatic snapshotting, VM deployment and management.
  - High availability
### VMware Workstation
- Organize VMs in folders.
- Finer controls over network adapters.
- 3D Graphics.
- Better performance.
### QEMU
- Known as Quick EMUlator.
- Emulate full systems (i.e., ARM on x86_x64 host) - ideal for emulating different hardware and environments.
- Arguably less user-friendly since it is used on the CLI.

<br>

#### Q1: What is the name of the Hypervisor that can be found as both a type 1 and type 2 Hypervisor?
<pre>Hyper-V</pre>
<br>

#### Q2: What is the name of the open-source Hypervisor developed by Oracle?
<pre>VirtualBox</pre>
<br>

## Task 4: Hypervisors in Cyber Security

#### Q1: As of the time of writing, what is the maximum amount that Microsoft offers for disclosed Hyper-V vulnerabilities?
<pre>$250,000</pre>
<br>

#### Q2: What category of use do cyber security analysts use Hypervisors to analyse malicious code?
<pre>Research</pre>
<br>

#### Q3: What is the name of one of the APT groups that has been identified as targeting ESXi Hypervisors?
<pre>ALPHAV</pre>
<br>

## Task 5: Hypervisor Internals
- vCPU (virtual CPU) are mapped to cores available on physical CPU.
- Best practice is to limit use of vCPUs (should be less than physical cores in use - prevents oversubscribing).
### Networking Types
- **Bridged**: Allows VM to appear as another device on host network.
- **NAT**: Guest network activity appears as if originating from host.
- **Host-only**: Only guest will be accesible from host itself.
- **Specific**: Manually assign vNIC used by guest - specify subnet and address range.
### Paravirtualization
- Guest VMs using paravirtualization are aware they are operating on virtualized hardware.
- Allows better performance - hardware isn't fully emulated.
- KVM uses combination of virtualization and paravirtualization to achieve its performance.
  - KVM is Kernel-based Virtual Machine. Built into Linux kernel.
### Nested Virtualization
- Allows for virtual machines within virtual machines.
- Achieved using Intel VT-x or AMD-V (features within CPU).
- Adds complexity and requires more computing resources to the guest.

<br>

#### Q1: What is the acronym for a virtual CPU?
<pre>vCPU</pre>
<br>

#### Q2: What is the acronym for a virtual network adapter?
<pre>vNIC</pre>
<br>

#### Q3: What virtualisation method allows for a Hypervisor to be ran within a virtual machine?
<pre>Nested virtualisation</pre>
<br>

## Task 6: Guest Additions
- Drivers and software used to enhance functionality and performance of a VM.
- Features:
  - Enhanced performance.
  - Shared folders.
  - Shared clipboard.
  - Improved graphics.
  - USB devices.
- Potentially increases risk of attack (i.e., ransomware can escape onto host with shared folders).

<br>

#### Q1: What is the full CVE of the vulnerability that allowed attackers to exploit guest additions to escape the guest environment? Format: CVE-XXXX-XXXX
<pre>CVE-2018-2693</pre>
<br>

#### Q2: What name does the VMware guest additions process show up as on the guest?
<pre>VMware Tools Core Service</pre>
<br>

## Task 7: Practical
The practical task is fairly simple - click and drag virtualisation components to correct parts of the diagram.

<br>

#### Q1: What is the flag from the practical?
<pre>THM{LAYERS_UPON_LAYERS}</pre>
