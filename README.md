# Cloud SOC 2.0 Lab

## Overview

After reading the blog series *"So You Want to Be a SOC Analyst"*, I decided to try out the **Cloud SOC 2.0 Lab** to get hands-on experience and see if I would enjoy working in security operations. This lab focused on building a cloud-based SOC environment, simulating real-world scenarios, and practicing threat detection and response using tools like Azure Sentinel and LimaCharlie.

---

## Lab Components

### 1. Environment Setup
- **Cloud-Based Virtual Machine**: Deployed a pre-configured, cloud-hosted virtual machine to serve as the primary environment, eliminating the need for local VM setups.
- **LimaCharlie EDR Integration**: Installed the LimaCharlie Endpoint Detection and Response (EDR) agent to monitor system activities and collect security telemetry.

### 2. Command and Control Simulation
- **Sliver C2 Framework**: Set up the Sliver Command and Control (C2) server within the virtual machine to simulate adversarial activities.
- **Payload Deployment**: Generated and executed payloads to establish C2 sessions, facilitating the simulation of common attack vectors.

### 3. Adversarial Activities
- **Privilege Escalation**: Performed actions to elevate privileges within the system, mimicking tactics used by malicious actors.
- **Credential Dumping**: Executed techniques to extract sensitive information, such as dumping the `lsass.exe` process, to understand potential data exposure risks.

### 4. Detection and Response
- **LimaCharlie Telemetry Analysis**: Monitored and analyzed security events generated by LimaCharlie to identify indicators of compromise.
- **Custom Detection Rules**: Developed and implemented rules to detect specific malicious activities, enhancing the system's threat detection capabilities.
- **Blocking Malicious Actions**: Configured automated responses to prevent identified threats, such as blocking the deletion of volume shadow copies—a common ransomware tactic.

### 5. Advanced Threat Detection
- **Automated YARA Scanning**: Integrated YARA rules into the environment to automatically scan for known malware signatures, improving the detection of malicious files and processes.

---

### Key Learnings

1. **Adversarial Simulations**  
   Used the Sliver C2 framework to simulate attacks like C2 sessions and reconnaissance, gaining insight into how attackers operate.  

2. **Detection and Response**  
   Built and tested detection rules in Azure Sentinel and monitored endpoint activity with LimaCharlie to identify and respond to malicious behavior.  

3. **Blocking Threats**  
   Implemented rules in LimaCharlie to block payload execution and prevent unauthorized access to sensitive processes like `lsass.exe`.  

4. **Building and Managing a Lab**  
   Set up a cloud-based lab with virtual machines and integrated tools to practice security monitoring, threat detection, and attack mitigation.




---

