# Keylogger-Implementation-and-Splunk-Analysis

## Executive Summary
This project explores the creation, deployment, and analysis of a keylogger in a controlled virtualized environment. Designed to understand both the ethical and technical implications of keylogger usage, the project emphasizes secure implementation and detailed analysis of collected data. By utilizing VirtualBox, the project replicated a target system to simulate real-world scenarios while adhering to ethical standards. The ultimate goal was to enhance knowledge of monitoring and threat detection using Splunk.


## Introduction
### Background
Keyloggers are widely regarded as one of the most common tools for monitoring system activities, often used in both legitimate and malicious scenarios. This project focuses on developing and analyzing a keylogger in a virtualized environment, providing insights into its functionality and implications. The controlled setup ensures that the project is conducted ethically while enabling a thorough understanding of keylogging techniques and their impact.

### Objective
<ins> The primary goals of this project were: </ins>

- To create a functional keylogger capable of monitoring and recording keystrokes in a secure and ethical environment.
- To simulate its deployment on a virtualized target machine hosted on VirtualBox.
- To analyze captured data to understand the operational flow of keyloggers and their detection through system logs.

### Scope
The scope of the project includes the development and deployment of the keylogger on a Windows-based virtual machine, testing its functionality, and analyzing the logs generated in Splunk. The project also explores detection techniques and mitigation strategies to understand keylogger vulnerabilities and countermeasures.


## Project Overview
### Architecture Design
<ins> The virtual environment consisted of: </ins>

- Target Machine (target-pc): A Windows virtual machine used for testing and running the keylogger.
- Development Machine: Used to code and compile the keylogger script.
- VirtualBox Environment: Provided isolation and control to ensure ethical implementation.

### Components
- Target Machine: Windows-based virtual machine.
- Keylogger Script: Written in Python, it captures keystrokes and stores the data locally.
- Logging and Analysis Tools: Used for reviewing captured data and understanding system behaviors.

## Methodology
### 1.Keylogger Development:

- Developed a Python-based keylogger using libraries like `pynput` to monitor keyboard input.
- Implemented data capture functionality to store keystrokes in a text file (`keyfile.txt`) for analysis.

### 2.Virtual Environment Setup:

- Configured VirtualBox to host the target machine.
- Ensured isolation between the host and guest systems for security.

### 3.Keylogger Deployment:

- Installed and executed the keylogger on the target machine.
- Simulated typical user activity to generate data for analysis.

### 4.Telemetry Collection and Analysis:

- Monitored system activities during keylogger execution by checking the `keyfile.txt` file and Splunk.
- Reviewed logs to identify key events and analyze system responses to the keylogger (`EventID:1 / EventID:11`).


## Testing and Validation
### Simulated Attack Scenarios
#### <ins> Brute Force Attack:</ins>

- Using the command:
#### `hydra -t 1 -w 10 -l msmith -P passwords.txt rdp://192.168.10.100`

- A brute force attack was conducted via Remote Desktop Protocol (RDP) targeting the msmith account. Upon successful login, event IDs such as 4625 (failed login), 4624 (successful login), 4634 (logoff), and 4776 (authentication attempt) were logged in Splunk. These logs provided crucial details about the attack sequence.

#### <ins> Network Scans:</ins>

- Nmap was utilized to identify open ports and services on the target machine. Sysmon captured unauthorized scanning activities, which Splunk dashboards highlighted for further analysis.


#### <ins> Installation of Atomic Red Team (ART): </ins>
To simulate MITRE ATT&CK techniques, Atomic Red Team was installed on the target Windows machine:

PowerShell Installation Execution:
The following command was executed in PowerShell (with administrator privileges) to install Atomic Red Team:

#### powershell:
`Install-AtomicRedTeam -getAtomics`


#### <ins> Defender Exclusions for Atomic Red Team: </ins>
- To prevent Microsoft Defender from blocking ART files, the entire C:\ drive was excluded via Windows Security:

#### Path: 
- Virus & Threat Protection > Manage Settings > Exclusions > Add Folder.
- Administrator privileges were required to confirm the exclusion.

#### <ins> Atomic Red Team Installation: </ins>
The following command downloaded and unpacked ART on the target system:

#### powershell:
`IEX (IWR 'https://raw.githubusercontent.com/redcanaryco/invoke-atomicredteam/master/install-atomicredteam.ps1' - UseBasicParsing);`
**Dependencies were installed by confirming prompts during setup.**

#### <ins> Testing MITRE ATT&CK Techniques: </ins>

- After installation, the C:\AtomicRedTeam\atomics directory provided access to technique IDs corresponding to MITRE ATT&CK techniques.
- For example, Technique ID T119 was explored for testing and mapped back to the MITRE ATT&CK Enterprise Matrix for further understanding.

### Log Analysis and Insights
- #### Event Detection:
  Splunk dashboards visualized real-time system activities, flagging anomalies such as repeated login attempts and unauthorized access.
- #### Correlated Events:
  Logs like Event ID 4625, 4624, 4634, and 4776 were analyzed to trace the attack path and determine its impact.
- #### Actionable Insights:
  Detailed event correlations helped identify the root cause of the attacks, enabling a better understanding of threat dynamics and response strategies.

## Conclusion
The Active Directory and Cybersecurity Project demonstrated the importance of integrating security practices with AD management. By simulating attacks and analyzing system responses, the project highlighted:

- The critical role of AD in enterprise security and its potential vulnerabilities.
- The effectiveness of telemetry tools like Sysmon in generating actionable security data.
- The value of log analysis platforms like Splunk in detecting and responding to incidents.

### Key Takeaways
- Active Directory requires continuous monitoring and robust security configurations to mitigate threats.
- Simulated attack scenarios are invaluable for understanding real-world adversarial techniques and improving defense mechanisms.
- Combining telemetry tools and SIEM platforms enhances incident detection and response capabilities.



## Figures

### Figure 1.
This diagram illustrates the logical layout of the components involved in the Active Directory and Cybersecurity project. It visualizes the flow of data and interactions between key components, including the domain controller (ADDC01), target machine, Kali Linux (used for attack simulations), and Splunk for log analysis. The diagram provides a clear overview of the project's architecture and serves as a blueprint for understanding the integration of offensive and defensive elements.


<img width="380" alt="Diagram" src="https://github.com/user-attachments/assets/e4bb13cf-cd81-40dd-af8c-a72ed9af44fc" />
