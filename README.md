# Assignment 1:

I performed this assignment without any other team member.

### Steps carried out for setup configuration:

For this particular series of assignments I chose my laptop itself (instead of using GCP or any other workstation) which runs Linux-Ubuntu OS and also has support for Nested Hardware Virtualization (found out by checking for 'vmx flags' in the output of command: 'cat /proc/cpuinfo')

However, to be more safe, I installed VMWare Workstation Pro and created an Ubuntu based VM inside it. Following were some features of the VM created,
- 30 day free license
- settings - ENABLE -> 'Virtualize Intel VT-x/EPT or AMD-V/RVI' (to enable support for Nested Virtualization)
- cat /proc/cpuinfo inside the VM confirms that VMX Flags are available in the VM
- Specs: 100GB, 8GB Memory, 4 vCPUs
- VM Created using Ubuntu 20.04 ISO Image


- Necessary dependencies like git, vim, make, gcc etc. were installed


- Forked the official Linux git repository into my github account; and then cloned the new repo into this VM

- Downloaded cmpe283-1.c and Makefile into this VM

- Include code changes for MODULE_LINCESE("GPL v2")

Run the following commands as mentioned below:
1. 'make' command in the location where cmpe283-1.c and Makefile are present i.e. outside the linux/ directory

2. Install all necessary dependencies with the command:
	> sudo apt install gcc bison flex libssl-dev
	> sudo apt-get install build-essential
	> sudo apt install elfutils libelf-dev

	'make clean' to clean what was made in the earlier step without some necessary dependecies. Hit the 'make' command again

3. cd linux/

4. 'make oldconfig' in the linux/ directory. Use all the default options by keeping the Enter key pressed (as suggested by Professor)

5. 'make prepare'

6. 'make -j 4 modules'

7. 'sudo make -j 4'
	- at this point I got the error: 'No rule to make target 'debian/canonical-certs.pem' needed by 'certs/x509_certificate_list'. Stop.

	- SOLUTION: Hit folllowing two commands
		- scripts/config --set-str SYSTEM_TRUSTED_KEYS ""
		- scripts/config --disable SYSTEM_REVOCATION_KEYS 
		- This is because the make config tries to sign the kernel modules with a Canonical Private key.

	- Hit the make command again after above fix

8. sudo make INSTALL_MOD_STRIP=1 modules_install
	- install all the modules, with the debugging info OFF as suggested.

9. make
	- This command took around 2 hrs 10 minutes!
	- At the end got an error like: 
		BTF: .tmp_vmlinux.btf: pahole (pahole) is not available
		Failed to generate BTF for vmlinux
		...
		...

	- But it was resolved using the command: sudo apt install dwarves


10. make install
	- ERROR: Missing file: arch/x86/boot/bzImage. /bib/sh: 1: zstd not found
	- SOLUTION: 
		- sudo apt-get install -y zstd
		- make bzImage

	- Run command again


11. sudo reboot

12. uname -a
	- Ubuntu 5.18.0-rc3+ kernel is now installed!!!!!!

13. cd ../

14. make 

15. sudo insmod cmpe283-1.ko

Make the necessary code changes in the cmpe283-1.c file to print the various MRS Control capabilities to the system message log and repeat the make process and insmod again.


### MSR Capabilities, code output:
```
[ 6568.652794] CMPE 283 Assignment 1 Module Start
[ 6568.652868] Pinbased Controls MSR: 0x3f00000016
[ 6568.653155]   External Interrupt Exiting: Can set=Yes, Can clear=Yes
[ 6568.653376]   NMI Exiting: Can set=Yes, Can clear=Yes
[ 6568.653377]   Virtual NMIs: Can set=Yes, Can clear=Yes
[ 6568.653377]   Activate VMX Preemption Timer: Can set=No, Can clear=Yes
[ 6568.653377]   Process Posted Interrupts: Can set=No, Can clear=Yes
[ 6568.653379] Primary Processor-Based VM-Execution Controls MSR: 0xfff9fffe0401e172
[ 6568.653379]   Interrupt-window exiting: Can set=Yes, Can clear=Yes
[ 6568.653380]   Use TSC offsetting: Can set=Yes, Can clear=Yes
[ 6568.653380]   HLT exiting: Can set=Yes, Can clear=Yes
[ 6568.653380]   INVLPG exiting: Can set=Yes, Can clear=Yes
[ 6568.653381]   MWAIT exiting: Can set=Yes, Can clear=Yes
[ 6568.653381]   RDPMC exiting: Can set=Yes, Can clear=Yes
[ 6568.653382]   RDTSC exiting: Can set=Yes, Can clear=Yes
[ 6568.653382]   CR3-load exiting: Can set=Yes, Can clear=No
[ 6568.653382]   CR3-store exiting: Can set=Yes, Can clear=No
[ 6568.653383]   Activate tertiary controls: Can set=No, Can clear=Yes
[ 6568.653383]   CR8-load exiting: Can set=Yes, Can clear=Yes
[ 6568.653383]   CR8-store exiting: Can set=Yes, Can clear=Yes
[ 6568.653384]   Use TPR shadow: Can set=Yes, Can clear=Yes
[ 6568.653384]   NMI-window exiting: Can set=Yes, Can clear=Yes
[ 6568.653384]   MOV-DR exiting: Can set=Yes, Can clear=Yes
[ 6568.653385]   Unconditional I/O exiting: Can set=Yes, Can clear=Yes
[ 6568.653385]   Use I/O bitmaps: Can set=Yes, Can clear=Yes
[ 6568.653386]   Monitor trap flag: Can set=Yes, Can clear=Yes
[ 6568.653386]   Use MSR bitmaps: Can set=Yes, Can clear=Yes
[ 6568.653386]   MONITOR exiting: Can set=Yes, Can clear=Yes
[ 6568.653387]   PAUSE exiting: Can set=Yes, Can clear=Yes
[ 6568.653387]   Activate secondary controls: Can set=Yes, Can clear=Yes
[ 6568.653388] Secondary Processor-Based VM-Execution Controls MSR: 0x553cfe00000000
[ 6568.653389]   Virtualize APIC accesses: Can set=No, Can clear=Yes
[ 6568.653389]   Enable EPT: Can set=Yes, Can clear=Yes
[ 6568.653390]   Descriptor-table exiting: Can set=Yes, Can clear=Yes
[ 6568.653390]   Enable RDTSCP: Can set=Yes, Can clear=Yes
[ 6568.653390]   Virtualize x2APIC mode: Can set=Yes, Can clear=Yes
[ 6568.653391]   Enable VPID: Can set=Yes, Can clear=Yes
[ 6568.653391]   WBINVD exiting: Can set=Yes, Can clear=Yes
[ 6568.653391]   Unrestricted guest: Can set=Yes, Can clear=Yes
[ 6568.653392]   APIC-register virtualization: Can set=No, Can clear=Yes
[ 6568.653392]   Virtual-interrupt delivery: Can set=No, Can clear=Yes
[ 6568.653393]   PAUSE-loop exiting: Can set=Yes, Can clear=Yes
[ 6568.653393]   RDRAND exiting: Can set=Yes, Can clear=Yes
[ 6568.653393]   Enable INVPCID: Can set=Yes, Can clear=Yes
[ 6568.653394]   Enable VM functions: Can set=Yes, Can clear=Yes
[ 6568.653394]   VMCS shadowing: Can set=No, Can clear=Yes
[ 6568.653394]   Enable ENCLS exiting: Can set=No, Can clear=Yes
[ 6568.653395]   RDSEED exiting: Can set=Yes, Can clear=Yes
[ 6568.653395]   Enable PML: Can set=No, Can clear=Yes
[ 6568.653395]   EPT-violation #VE: Can set=Yes, Can clear=Yes
[ 6568.653396]   Conceal VMX from PT: Can set=No, Can clear=Yes
[ 6568.653396]   Enable XSAVES/XRSTORS: Can set=Yes, Can clear=Yes
[ 6568.653397]   Mode-based execute control for EPT: Can set=Yes, Can clear=Yes
[ 6568.653397]   Sub-page write permissions for EPT: Can set=No, Can clear=Yes
[ 6568.653398]   Intel PT uses guest physical addresses: Can set=No, Can clear=Yes
[ 6568.653398]   Use TSC scaling: Can set=No, Can clear=Yes
[ 6568.653398]   Enable user wait and pause: Can set=No, Can clear=Yes
[ 6568.653399]   Enable ENCLV exiting: Can set=No, Can clear=Yes
[ 6568.653400] VM-Exit Controls MSR: 0x3fefff00036dff
[ 6568.653400]   Save debug controls: Can set=Yes, Can clear=No
[ 6568.653401]   Host address-space size: Can set=Yes, Can clear=Yes
[ 6568.653401]   Load IA32_PERF_GLOBAL_CTRL: Can set=No, Can clear=Yes
[ 6568.653402]   Acknowledge interrupt on exit: Can set=Yes, Can clear=Yes
[ 6568.653402]   Save IA32_PAT: Can set=Yes, Can clear=Yes
[ 6568.653402]   Load IA32_PAT: Can set=Yes, Can clear=Yes
[ 6568.653403]   Save IA32_EFER: Can set=Yes, Can clear=Yes
[ 6568.653403]   Load IA32_EFER: Can set=Yes, Can clear=Yes
[ 6568.653411]   Save VMX-preemption timer value: Can set=No, Can clear=Yes
[ 6568.653513]   Clear IA32_BNDCFGS: Can set=No, Can clear=Yes
[ 6568.653514]   Conceal VMX from PT: Can set=No, Can clear=Yes
[ 6568.653540]   Clear IA32_RTIT_CTL: Can set=No, Can clear=Yes
[ 6568.653631]   Clear IA32_LBR_CTL: Can set=No, Can clear=Yes
[ 6568.653682]   Load CET state: Can set=No, Can clear=Yes
[ 6568.653683]   Load PKRS: Can set=No, Can clear=Yes
[ 6568.653826]   Activate secondary controls: Can set=No, Can clear=Yes
[ 6568.653910] VM-Entry Controls MSR: 0xd3ff000011ff
[ 6568.654028]   Load debug controls: Can set=Yes, Can clear=No
[ 6568.654146]   IA-32e mode guest: Can set=Yes, Can clear=Yes
[ 6568.654197]   Entry to SMM: Can set=No, Can clear=Yes
[ 6568.655501]   Deactivate dualmonitor treatment: Can set=No, Can clear=Yes
[ 6568.655559]   Load IA32_PERF_GLOBAL_CTRL: Can set=No, Can clear=Yes
[ 6568.655585]   Load IA32_PAT: Can set=Yes, Can clear=Yes
[ 6568.655675]   Load IA32_EFER: Can set=Yes, Can clear=Yes
[ 6568.655765]   Load IA32_BNDCFGS: Can set=No, Can clear=Yes
[ 6568.655868]   Conceal VMX from PT: Can set=No, Can clear=Yes
[ 6568.655869]   Load IA32_RTIT_CTL: Can set=No, Can clear=Yes
[ 6568.655979]   Load CET state: Can set=No, Can clear=Yes
[ 6568.656043]   Load guest IA32_LBR_CTL: Can set=No, Can clear=Yes
[ 6568.656076]   Load PKRS: Can set=No, Can clear=Yes
[ 6582.511090] CMPE 283 Assignment 1 Module Exits
```


# Assignment 2

I performed this assignment without any other team member.

### Setup steps

Since, Nested Virtualization was enabled in the setup configuration during Assignment 1, I was able to create another VM inside my VMWare Workstation's VM using the following steps:

	1. Install Qemu KVM and virt-manager (and the necessary dependencies) using the following commands:
		> sudo apt-get update -y
		> sudo apt install qemu-kvm libvirt-daemon-system libvirt-clients bridge-utils virtinst virt-manager

	2. Check if the virt-manager is working using the either of the following commands:
		> systemctl status libvirtd
		OR
		> sudo systemctl is-active libvirtd

	3. Make sure you have downloaded the Ubuntu ISO Image file
	
	4. > sudo rmmod kvm_intel
           > sudo rmmod kvm
           > lsmod | grep kvm
           > sudo modprobe kvm
           > sudo modprobe kvm_intel

	5. Create an Ubuntu-VM by starting the QEMU Virt-Manager and following some basic UI prompts

	6. Install CPUID package into this VM using the following command:
		> sudo apt-get install -y cpuid

We now have the setup ready for testing our kernel code changes.


### <u>Code Changes</u>

For the Assignment 2, as we were allowed to choose among the four CPUID leaf nodes, I have selected the nodes 0x4FFFFFFF and 0x4FFFFFFE.

I have made the necessary changes in the files: /linux/arch/x86/kvm/cpuid.c and /linux/arch/x86/kvm/vmx/vmx.c using global variable approach.

For the changes in kernel code to take effect, we should follow the below steps:

	1. sudo make -j 4 modules
	
	2. sudo make INSTALL_MOD_STRIP=1 modules_install
	
	3. sudo make install 
	
	4. sudo reboot 

	(Step 3 could be optional)


### <u>Testing the code</u>
------------------

Start the Ubuntu-VM that was created earlier in Qemu Virt-manager.

Open a terminal and make following calls to the CPUID passing the leaf node values as paramters to it using the -l flag.
> cpuid -l 0x4FFFFFFF
> cpuid -l 0x4FFFFFFE

Check the output values in EAX, EBX and ECX Registers in the terminal for the second command.

Check the System Message log using the 'dmesg' command in a terminal in the parent VM (which is running on VMWare Workstation in my case). This log will contain the stats regarding the exits, i.e. 'Total number of exits' and 'Total time For all exits', which are the logs from the cpuid.c file.


#Assignment 3
-------------

Question 1: I did this assignment by myself

Setup steps:
-------------
- sudo rmmod kvm-intel
- sudo rmmod kvm

- Issue:
	- make -j 4 modules 
	- sudo make INSTALL_MOD_STRIP=1 modules_install && make install 
	- modprobe kvm
	- modprobe kvm-intel

	These commands did not work for me for some reason. I even tried running them after cleaning the make builds (i.e. 'make clean'); even then my code changes weren't refecting in the kernel.

	Solution: Explicitly 'make' the 'kvm' modules only (since code changes were made into kvm's cpuid.c and kvm/vmx's vmx.c only); using the following commands:
		- make M=arch/x86/kvm modules
		- insmod arch/x86/kvm/kvm.ko
		- insmod arch/x86/kvm/kvm-intel.ko

- Before making code changes we need to identify which exit types are not supported, by referring to SDM Manual (Page number 4281 - Volume 3-d Table C-1)

- Once the modules are loaded, start the inner vm and trigger the respective exits using the cpuid commands as below:
	- cpuid -l 0x4ffffffd -s <EXIT_NUMBER>
	- cpuid -l 0x4ffffffc -s <EXIT_NUMBER>

- To test the command in a loop for all integers in range [0-69], we can run a shell command as follows:
	- for i in `seq 0 69`; do cpuid -l 0x4ffffffd -s $i; done


- Check the system message logs using the below command:
	- dmesg



On a Full VM Boot, total number of exits observed was 1299672 which had a total processing time of 46950089552 cycles. Following were the most frequently occurring exit types

EPT violation EXIT (48) - 685299 
I/O instruction (30) - 145063, CPUID (10) - 140738
WRMSR (32) - 91609


Following was the distribution of the rest of the non-zero exit count occurences

0 - 8798
1 - 47966
7 - 9586
10 - 140738
12 - 30006
28 - 19537
30 - 145063
32 - 91609
40 - 3184
48 - 685299
49 - 27976

Looking at this distribution we can't exactly say that the exit counts increases in a constant or a linear fashion; but it does increase overall.


#Assignment 4
--------------------

Question 1: I did this assignment by myself


Steps:
-------
- Once the VM starts, get the total count using the 0x4fffffff cpuid exit
- Execute the 0x4ffffffd exit for range 0-69, using the command used in assignment 3. This will be the output for ept not being zero
- Shutdown the inner vm
- Remove the kvm-intel module: sudo rmmod kvm-intel
- Insert the module again using sudo insmod /lib/modules/5.18.0-rc3+/kernel/arch/x86/kvm/kvm-intel.ko ept=0 command. Record the outputs using the same procedure.

Nested Paging - With EPT
--------------------------

Total Number of exits = 1195689

Distribution of other non-zero count exit occurrences:
0 - 8801
1 - 46288
7 - 10103
10 - 140841
12 - 21574
28 - 19567
29 - 2
30 - 155787
31 - 571
32 - 78604
40 - 3016
48 - 693838
49 - 27093
54 - 3

Shadow paging - Without EPT (ept = 0)
------------------------------------------

Total Number of exits = 3808755

Distribution of other non-zero count exit occurrences:
0 - 8811
1 - 52669
7 - 11979
10 - 143671
12 - 32307
28 - 19567
29 - 2
30 - 156932
31 - 868
32 - 110199
40 - 3586
48 - 706080
49 - 30724
54 - 4
55 - 3

- Screenshots are added in the cmpe283 folder.

- Learning from the count of exits was that the shadow paging mode incurs more number of exits. The count was pretty much expected to increase as compared to the Nested Paging mode.
- Total number of exits is almost 3 times in shadow paging. This is expected to happen as the three exit types namely: CR3, Page Fault, and TLB Flush; are enabled in this mode.
- The exit number 48 has the highest count in both the modes
- If we observe, it seems that some exits have a similar count in both the modes for eg. exit numbers 30 and 10; however for others, there is a considerable increase in the shadow paging mode



