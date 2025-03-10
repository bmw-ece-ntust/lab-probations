---
title: Installation Guide for OAI 5G SA - Linux

---

![](https://i.imgur.com/JORnn3y.png =150x)@NTUST
# 
>[name=Ravi][color=#38c16a]

## Installation Guide for OAI 5G SA - Linux
### System requirements :

* No of PCs: 1 PC or 2 PCs. Note: If you plan to setup both OAI RAN and OAI Core (OAI CN5G) on the same system, you need one PC otherwise Two PCs.)
:::info
* Laptop/Desktop/Server for OAI CN5G and OAI gNB
            Operating System: Ubuntu 22.04 LTS
            CPU: 8 cores x86_64 @ 3.5 GHz
            RAM: 32 GB
:::


**Important:** *Setting Low latency Kernel and Other parameters on Laptop/Desktop/Server for OAI CN5G and OAI gNB.*

* Check [Kernek Requirement.](https://gitlab.eurecom.fr/oai/openairinterface5g/-/wikis/OpenAirKernelMainSetup#ubuntu-1604-ltslinux-kernel-version-48-or-higher)

Specific Features and Why to Disable Them:

**C-States (Idle States):** C-States allow the CPU to enter lower power modes when idle. Disabling them ensures the CPU remains in its active state and doesn't enter these power-saving states, which might lead to latency or performance issues when transitioning back to full power.

**P-States (Performance States):** P-States adjust the CPU's power consumption and performance depending on workload demands. Disabling P-States forces the CPU to run at maximum performance all the time.

1. You can disable **C-States** by adding specific kernel parameters at boot time.

Edit the GRUB configuration:

Open the GRUB configuration file:

       `sudo nano /etc/default/grub`

Modify the GRUB_CMDLINE_LINUX line to add intel_idle.max_cstate=0 (for Intel CPUs) or processor.max_cstate=1 (for AMD CPUs) to disable C-States. Example for Intel CPUs:

        `GRUB_CMDLINE_LINUX="intel_idle.max_cstate=0"`
        
2. Disabling P-States (CPU Frequency Scaling)

P-States are used to adjust the CPU frequency depending on the workload, allowing the CPU to run at lower frequencies for power saving. To disable P-States, you can force the CPU to operate at its maximum frequency at all times.
Method 1: Using the cpupower Tool

A- Install cpupower: If it's not already installed, install the cpupower utility:

    `sudo apt install linux-tools-common linux-tools-$(uname -r)`

B- Set the CPU governor to performance: The performance governor forces the CPU to run at the maximum frequency. Run the following command to apply this setting:

    `sudo cpupower frequency-set --governor performance`

C- erify the setting: You can check the current governor and CPU frequencies using:

    `cpupower frequency-info`


