# Sysmon-Mimikatz-VM-Lab
Sysmon Installation and Mimikatz Testing on Windows 11 VM
This repository provides a step-by-step guide for installing Sysmon on a Windows 11 virtual machine and using Mimikatz to generate security alerts for monitoring.

Table of Contents
Prerequisites
Setup
1. Create Windows 11 Virtual Machine
2. Install Sysmon
3. Configure Sysmon
4. Install Mimikatz
Generate Alerts with Mimikatz
Monitoring Alerts
Disclaimer
Prerequisites
A hypervisor or virtualization software (e.g., VMware, VirtualBox, Hyper-V).
A Windows 11 ISO or pre-built virtual machine image.
Administrative access to the Windows 11 VM.
Sysinternals Sysmon tool Download here.
Mimikatz executable Download here.
Warning: Use Mimikatz responsibly and only in a controlled environment like a virtual machine for testing purposes.

Setup
1. Create Windows 11 Virtual Machine
Install a hypervisor of your choice (e.g., VMware, VirtualBox, Hyper-V).
Create a new virtual machine and allocate sufficient resources (e.g., 2 CPU cores, 4GB RAM, 60GB disk).
Install Windows 11 using the ISO file or pre-built VM image.
Complete the initial setup and update Windows 11.
2. Install Sysmon
Download the Sysmon tool from the Sysinternals website.
Extract the downloaded zip file to a folder on your VM.
Open a Command Prompt as Administrator and navigate to the extracted folder.
Run the following command to install Sysmon:
cmd
Copy code
sysmon -accepteula -i sysmonconfig-export.xml
You can use the default configuration file provided or create your custom configuration.

3. Configure Sysmon
Create or modify the sysmonconfig-export.xml configuration file to include desired logging and monitoring rules.
To update the Sysmon configuration without reinstalling, use:
cmd
Copy code
sysmon -c sysmonconfig-export.xml
Verify Sysmon is running correctly by checking the Event Viewer under Applications and Services Logs > Microsoft > Windows > Sysmon.
4. Install Mimikatz
Download Mimikatz from the official GitHub repository.
Extract the Mimikatz archive to a folder on your VM.
Open a Command Prompt as Administrator and navigate to the extracted folder.
Generate Alerts with Mimikatz
Run Mimikatz to simulate malicious activities that Sysmon should detect. For example, to list user credentials, execute:
cmd
Copy code
.\mimikatz.exe
Then in the Mimikatz prompt, run:
mimikatz
Copy code
sekurlsa::logonpasswords
Check the Event Viewer to ensure Sysmon is capturing the events. Look for alerts under Applications and Services Logs > Microsoft > Windows > Sysmon.
Monitoring Alerts
Use a SIEM (Security Information and Event Management) solution to aggregate and monitor logs.
Configure alert rules in your SIEM based on Sysmon logs to detect and respond to suspicious activities.
Disclaimer
This guide is intended for educational and testing purposes only. Misuse of Mimikatz and similar tools can lead to legal consequences. Always ensure you have proper authorization before conducting any security testing or assessments.
