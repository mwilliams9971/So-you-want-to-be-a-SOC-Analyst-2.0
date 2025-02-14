# Detection and Blocking Rules

This document outlines the detection and blocking rules explicitly mentioned in Part 3 and Part 4 of the SOC Analyst 2.0 Lab.

## Detection Rule

### Detect Sensitive Process Access
- **Rule Logic**:
    ```
    event: SENSITIVE_PROCESS_ACCESS
    op: and
    rules:
      - op: ends with
        path: event/*/TARGET/FILE_PATH
        value: lsass.exe
      - not: true
        op: ends with
        path: event/*/SOURCE/FILE_PATH
        value: wmiprvse.exe
    ```

- **Purpose**: Detect unauthorized access to sensitive processes, such as `lsass.exe`, while excluding legitimate access by system processes like `wmiprvse.exe`.

- **Alert Configuration**:
  - Generate an alert when any process other than `wmiprvse.exe` attempts to access `lsass.exe`.

---

## Blocking Rules

### 1. Block Execution of Payload
- **Rule Logic**:
    ```
    event: NEW_PROCESS
    op: and
    rules:
      - op: ends with
        path: event/*/FILE_PATH
        value: [your_C2-implant.exe]
    response: BLOCK
    ```

- **Purpose**: Automatically block the execution of the Sliver implant payload to prevent further compromise.

- **Action**:
  - Implemented a response to block processes that match the payload name.

---

### 2. Block Credential Access via LSASS
- **Rule Logic**:
    ```
    event: SENSITIVE_PROCESS_ACCESS
    op: and
    rules:
      - op: ends with
        path: event/*/TARGET/FILE_PATH
        value: lsass.exe
      - not: true
        op: ends with
        path: event/*/SOURCE/FILE_PATH
        value: wmiprvse.exe
    response: BLOCK
    ```

- **Purpose**: Block unauthorized access to the `lsass.exe` process to prevent credential dumping.

- **Action**:
  - Added a response to block all processes attempting unauthorized access to `lsass.exe`.

---

For further details, refer to the following guides:
- [Part 3: Let’s Get Adversarial](https://detailed-leo-854.notion.site/Part-3-Let-s-Get-Adversarial-47cb67336af348c890bce7336669e4fb)
- [Part 4: Blocking Attacks](https://detailed-leo-854.notion.site/Part-4-Blocking-Attacks-47ee3dacc5994cee90c79e54d9c6cfcc)
