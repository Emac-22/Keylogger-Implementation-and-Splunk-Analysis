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
### Simulated Scenarios:


#### <ins> Keystroke Capture:</ins>

- Typed various inputs on the target machine to evaluate the keylogger's accuracy in recording keystrokes.
- Verified stored logs to ensure all inputs were captured without loss.


#### <ins> Detection Testing:</ins>

- Injested and analyzed logs using Sysmon to trace keylogger activities.
- Identified Event IDs (`EventID:1 / EventID:11`) linked to the keylogger’s execution and data storage.



### Log Analysis and Insights
- #### Event Detection:
  Key system activities, such as file creation and keyboard input monitoring, were logged.
- #### Correlated Events:
  Logs provided a timeline of keylogger activities, from execution to data capture.
- #### Actionable Insights:
  Analysis highlighted potential system vulnerabilities and detection opportunities, demonstrating how monitoring tools can identify unauthorized keylogging activity.

## Conclusion
The Keylogger `Implementation and Splunk Analysis Project` provided valuable insights into the ethical and technical aspects of keylogger usage. Through development, deployment, and analysis, the project demonstrated:

- The functionality of keyloggers in capturing system activities.
- The importance of controlled environments for ethical testing.
- The value of system logs in detecting unauthorized monitoring tools.

### Key Takeaways

- Robust logging mechanisms, such as Sysmon and Event Viewer, proved invaluable in tracing the activities of the keylogger, highlighting their role in threat detection and 
  incident response.
- The hands-on implementation strengthened technical skills in Python programming, virtualized environment setup, and log analysis, aligning with industry-relevant 
  cybersecurity practices.
- The ability to monitor endpoint activities in real time played a crucial role in identifying and understanding the impact of the keylogger, reinforcing the value of EDR 
  (Endpoint Detection and Response) tools.
- Analyzing event logs demonstrated how keylogger activities correlate with specific system behaviors, such as process execution and file creation, improving threat-hunting 
  skills.



## Figures

### Figure 1.
This diagram illustrates the logical layout of the components involved in the Active Directory and Cybersecurity project. It visualizes the flow of data and interactions between key components, including the domain controller (ADDC01), target machine, Kali Linux (used for attack simulations), and Splunk for log analysis. The diagram provides a clear overview of the project's architecture and serves as a blueprint for understanding the integration of offensive and defensive elements.


<img width="380" alt="Diagram" src="https://github.com/user-attachments/assets/e4bb13cf-cd81-40dd-af8c-a72ed9af44fc" />
