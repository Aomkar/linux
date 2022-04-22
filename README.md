Assignment 1:
==============



# MSR Capabilities, code output:
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
