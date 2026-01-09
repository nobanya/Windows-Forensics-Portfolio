# Windows Event Log Analysis For Incident Response

## Overview
Windows Event Logs provide critical visibility into system activity and user behavior. In this project, I performed hands on analysis of Windows Event Logs to identify and investigate potential security incidents. The objective was to build practical experience accessing, filtering, parsing, and correlating event data to detect suspicious behavior and support incident investigation.

## Lab Environment
To complete this project, I used a Windows operating system. The lab can be performed on either a physical system or a virtual machine using platforms such as VirtualBox or VMware.

### Pre-requisites
- Basic understanding of the Windows operating system  
- Familiarity with command-line usage  
- Administrative access to the Windows system  

### Tools Used
The following tools were used throughout this project:
1. **Event Viewer** – Native Windows utility for viewing and filtering event logs  
2. **PowerShell** – Used to automate log querying and export results  
3. **Log Parser** – Microsoft tool for structured event log analysis  

#### Installing Log Parser
1. Download Log Parser from the [Microsoft Download Center](https://www.microsoft.com/en-us/download/details.aspx?id=24659).
2. Run the installer and complete the installation using the default settings.

## Exercises

### Exercise 1: Accessing Windows Event Logs with Event Viewer
**Objective**: Navigate Windows Event Logs and identify authentication-related activity.

**Steps**:
1. Open Event Viewer:
   - Press `Win + R`, type `eventvwr.msc`, and press `Enter`.
2. Browse available log categories:
   - Expand `Windows Logs` to view Application, Security, Setup, System, and Forwarded Events.
3. Review authentication activity:
   - Select `Security` under `Windows Logs`.
   - Examine events related to login attempts for signs of suspicious behavior.

**Expected Output**: Ability to navigate Windows Event Logs and recognize different event types, with emphasis on Security log entries.

---

### Exercise 2: Filtering and Exporting Event Logs
**Objective**: Isolate specific security events and export them for deeper analysis.

**Steps**:
1. Open Event Viewer and select the `Security` log.
2. Apply a filter for failed login attempts:
   - Right-click `Security` and select `Filter Current Log`.
   - Enter `4625` in the `Event ID` field.
   - Click `OK`.
3. Export the filtered results:
   - Right-click the filtered log and select `Save Filtered Log File As`.
   - Save the file as `FailedLogins.evtx`.

**Expected Output**: Filtered Security events containing failed login attempts saved to a standalone event log file.

---

### Exercise 3: Parsing Event Logs with Log Parser
**Objective**: Extract structured data from Windows Event Logs.

**Steps**:
1. Open Command Prompt and navigate to the Log Parser installation directory.
2. Execute the following command to parse failed login events:
   ```sh
   LogParser.exe "SELECT TimeGenerated, EventID, EventTypeName, Message INTO FailedLogins.csv FROM FailedLogins.evtx" -i:EVT -o:CSV
   ```
3. Open the FailedLogins.csv file to review the extracted data.

**Expected Output**: A CSV file containing timestamped and structured details of failed login attempts.

### Exercise 4: Analyzing Event Logs Using PowerShell

**Objective**: Automate log analysis using PowerShell.

**Steps**:

1. Open PowerShell with administrative privileges.

2. Run the following command to display failed login events:
```powershell
Get-WinEvent -FilterHashtable @{LogName='Security'; Id=4625} | Format-Table TimeCreated, Id, Message -AutoSize
```

3. Save the results to a text file:
```powershell
Get-WinEvent -FilterHashtable @{LogName='Security'; Id=4625} | Format-Table TimeCreated, Id, Message -AutoSize | Out-File -FilePath FailedLogins.txt
```

**Expected Output**: Failed login attempts displayed in the console and saved to a text file for documentation and review.

### Exercise 5: Correlating Events for Incident Analysis

**Objective**: Correlate authentication events to identify suspicious login patterns.

Steps:

1. Open Event Viewer and access the Security log.

2. Identify successful logins (Event ID 4624) and compare them with failed attempts (Event ID 4625).

3. Correlate the events using Log Parser:
```sh
LogParser.exe "SELECT a.TimeGenerated AS FailedLoginTime, b.TimeGenerated AS SuccessfulLoginTime, a.Message AS FailedLoginMessage, b.Message AS SuccessfulLoginMessage INTO CorrelatedLogins.csv FROM FailedLogins.evtx a JOIN SuccessfulLogins.evtx b ON a.User=b.User WHERE a.EventID=4625 AND b.EventID=4624" -i:EVT -o:CSV
```

4. Review the CorrelatedLogins.csv file to identify anomalies or patterns.

**Expected Output**: Correlated authentication events providing visibility into failed logins followed by successful access attempts.

### Outcome

Through this project, I gained hands on experience investigating Windows Event Logs using native tools and supplemental utilities. The exercises strengthened my ability to detect suspicious authentication activity, automate log analysis, and correlate events to support security incident investigations. 
