# Environment Details

This document describes the infrastructure and configurations used in the SOC Analyst 2.0 Lab environment.

---

## 1. Overview of the Lab Environment
The lab is designed to simulate a real-world Security Operations Center (SOC) with components for detection, analysis, and response to adversarial activities. Key components include:
- **Azure Sentinel**: Centralized SIEM for log ingestion, detection rules, and incident response.
- **LimaCharlie**: Endpoint Detection and Response (EDR) for telemetry and malware analysis.
- **Sliver C2**: Command and Control framework for simulating adversarial behavior.

---

## 2. Azure Virtual Machines
Two virtual machines were provisioned in Azure to simulate the attack and defense environment:
- **Windows VM**:
  - **Purpose**: Target system for adversarial simulations and telemetry collection.
  - **Specifications**:
    - OS: Windows 10
    - CPU: 2 vCPUs
    - Memory: 8 GB
  - **Tools Installed**:
    - Sliver C2 implant (payload execution)
    - LimaCharlie Agent
    - Administrative tools (PowerShell, Command Prompt).

- **Ubuntu VM**:
  - **Purpose**: Host for the Sliver C2 server.
  - **Specifications**:
    - OS: Ubuntu 20.04 LTS
    - CPU: 2 vCPUs
    - Memory: 4 GB
  - **Tools Installed**:
    - Sliver C2 framework
    - OpenSSH for secure remote acce
