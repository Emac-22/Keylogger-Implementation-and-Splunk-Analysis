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

### <ins>Figure 1: Installation and Verification of Pynput Library</ins>
This figure demonstrates the successful installation and verification of the Pynput library, a Python module used for controlling and monitoring input devices such as keyboards and mice. The installation was performed using the command:

`py -m pip install pynput`

<img width="359" alt="pip install" src="https://github.com/user-attachments/assets/07494592-6cbd-4ccc-baeb-27ef93df54d9" />


After the installation, the command:

`py -m pip show pynput`


<img width="384" alt="Success Install pip" src="https://github.com/user-attachments/assets/58891eee-d6dc-4c77-b070-2c25e1a5a242" />


### <ins>Figure 2: Keylogger Code Implementation</ins>

This figure showcases the Python code used to implement a basic keylogger. Utilizing the Pynput library, the script monitors and logs keyboard input into a file named `keyfile.txt`. The key functionalities of the code are described below:

#### Importing the Library:
- The `keyboard` module from the Pynput library is imported, enabling the script to listen for and process keystrokes.

#### Defining the Key Press Function:
The `keyPressed` function captures each key pressed by the user.

- The key is converted to a string representation using `str(key)` for immediate output.
- The key is written to a file, `keyfile.txt`, in append mode. A `try-except` block ensures the function gracefully handles any errors, such as when non-character keys 
  (e.g., Shift, Ctrl) are pressed.

#### Setting Up the Listener:
- The `keyboard.Listener` class is instantiated with the `on_press` parameter linked to the `keyPressed` function. The `start()` method initiates the key listener, while 
  the `input()` function ensures the program remains active and responsive to user input.

This code serves as the foundation for capturing keystrokes and logging them securely, demonstrating a practical application of Pynput in monitoring keyboard activity.

<img width="508" alt="Keylogger Code" src="https://github.com/user-attachments/assets/bda9e86c-7de0-4f8e-8772-4880630cbc18" />


### <ins>Figure 3: Keylogger in Action – Capturing and Logging Keystrokes</ins>
This figure demonstrates the functionality of the keylogger by showing the process of capturing and logging typed input.

#### Typing "Hello World" in the VSCode Terminal:
- The first image illustrates the user typing the phrase `"Hello World"` into the Visual Studio Code (VSCode) terminal. Each key press is detected by the keylogger script running in the background.

 <img width="381" alt="Hello World Terminal" src="https://github.com/user-attachments/assets/3cc021dc-77c6-4579-b982-4b1fd6688098" />
 

#### Logged Output in keyfile.txt:
- The second image displays the contents of the `keyfile.txt` file, opened in Notepad. The file shows the phrase `"HelloWorld"`—a precise recording of the typed input. Note that spaces are not captured in the current implementation, reflecting the program's behavior based on the keyPressed function design.

<img width="508" alt="Hello World text" src="https://github.com/user-attachments/assets/b0ae2382-07d6-4074-9a63-5b3fb15670c9" />


### <ins>Figure 4: Keylogger Demonstration – Simulating Credential Capture</ins>
This figure showcases the keylogger's ability to record user input, demonstrating a simulated credential capture scenario.

#### Simulated User Input in Google Search:
- The first image shows the user typing "Instagram" into the Google search bar, followed by `"User1"` and `"Password123"` in the search field. This simulation represents a 
  scenario where a user might enter their credentials for logging into a website.

  <img width="508" alt="Login Try" src="https://github.com/user-attachments/assets/a317fb8c-b522-414d-a7cb-7d56ca52c995" />


#### Logged Output in keyfile.txt:
- The second image displays the updated contents of the `keyfile.txt` file, opened in Notepad. The file now shows:
 `"HelloWorldInstagramUser1Password123"`
- This reflects the sequential capture of all typed inputs, including the previously logged `"HelloWorld"`.

This example demonstrates the keylogger's ability to log potentially sensitive user input such as credentials. It underscores the importance of understanding how such tools work to evaluate the associated risks and implement necessary safeguards.


 <img width="509" alt="Keylogger Read" src="https://github.com/user-attachments/assets/0382bc17-7e6b-4944-bc29-3c1a91a71d06" />


 
### <ins>Figure 5: Integration with Splunk – Keylogger Event Logging and Analysis</ins>
This figure illustrates the successful integration of the keylogger project with Splunk for event logging and monitoring using Sysmon-generated logs. Screenshots demonstrate the visibility of keylogger-related activities in the Splunk viewer.

#### Search Results for index="endpoint" keylogger:
The first screenshot shows a search query executed in Splunk for `index="endpoint" keylogger`, revealing keylogger-related events captured from the endpoint. This confirms that the inputs configured in the Sysmon `inputs.conf` file successfully routed data to Splunk.

<img width="510" alt="Splunk Events" src="https://github.com/user-attachments/assets/682d2dc9-29ac-4ed5-99b1-d4b35030f6f0" />


#### Event ID Analysis – Event IDs 11 and 1:
The second screenshot highlights the detection of `Event IDs 11 (File Create) and 1 (Process Creation)` associated with keylogger operations. These events provide detailed telemetry about system activities linked to the keylogger's functionality.

<img width="507" alt="EventID 1 Splunk" src="https://github.com/user-attachments/assets/64a76a81-0c1d-43ec-9b96-7414bdcdf4db" />

<img width="508" alt="EventID Splunk" src="https://github.com/user-attachments/assets/c1579433-6cef-4358-8dd0-b980ebb5f0d8" />



#### Search Query for Specific File Path:
Another screenshot demonstrates a more granular search, `index="endpoint" keylogger C:\\Users\msmith`, showcasing events related to the specific path where the `keyfile.txt` file is stored. This level of detail helps trace the keylogger's activities to its associated files.

<img width="509" alt="Keylogger Data Splunk" src="https://github.com/user-attachments/assets/c947c21e-8798-4fd5-9aaf-463a2985be97" />


#### Host Identification – TARGET-PC:
The final screenshot displays the host `TARGET-PC`, confirming the origin of the captured logs. Viewing these events from the `ADDC01` Active Directory server from my last Active Directory project and validates the centralized log collection and monitoring setup.

<img width="491" alt="Splunk Host" src="https://github.com/user-attachments/assets/bc0275b5-13c1-416f-9d9a-992d6f5821ac" />


These figures illustrate how Sysmon and Splunk were utilized to monitor and analyze the keylogger's behavior, emphasizing the importance of telemetry and SIEM tools in detecting and responding to such activities.
 

## References
Keylogger Python code retrieved from https://youtu.be/mDY3v2Xx-Q4?si=GN89uj9S4170TNVG

## Final Note
This project underscores the importance of ethical practices and creating a safe, controlled environment when conducting cybersecurity labs. Activities such as keylogging simulations and event analysis should always be performed on systems you own or have explicit permission to use, such as virtual environments like VirtualBox. These practices ensure compliance with ethical and legal standards while fostering a secure learning experience.

By utilizing dedicated virtual machines, tools like Sysmon, and monitoring platforms like Splunk, this lab provided a hands-on approach to understanding keylogger functionality and its detection. Such controlled experiments are invaluable for honing cybersecurity skills while maintaining responsible practices that align with professional integrity and industry standards
