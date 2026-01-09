# Windows Registry Forensics For Threat Detection

## Overview
The Windows Registry is a core component of the operating system that stores configuration data for both Windows and installed applications. In this project, I performed hands-on registry analysis to uncover indicators of malicious activity during a forensic investigation. Using the Volatility framework, I examined registry hives extracted from a memory image to identify user artifacts, persistence mechanisms, and suspicious behavior.

## Lab Environment
To complete this project, I worked with a Windows system and a captured memory image for forensic analysis. The lab can be performed on either a physical host or a virtual machine created with platforms such as VirtualBox or VMware.

### Pre-requisites
- Basic understanding of Windows OS internals and the Windows Registry  
- Familiarity with command-line operations  
- Administrative access on the Windows system  

### Tools Used
This project was completed using the following tool:
1. **Volatility** – An advanced memory forensics framework used for analyzing memory images.

#### Installing Volatility
1. Download Volatility from the [official website](https://www.volatilityfoundation.org/releases).
2. Extract the downloaded archive to a directory of your choice.
3. Verify that Python is installed on the system, as Volatility is compatible with Python 2.7.

## Exercises

### Exercise 1: Extracting Windows Registry Hives from a Memory Image
**Objective**: Extract Windows Registry hives from a memory image using Volatility.

**Steps**:
1. Open a command prompt and navigate to the Volatility directory.
2. Identify the correct profile for the memory image:
   ```sh
   volatility -f <memory_image> imageinfo
   ```
3. List available registry hives using the hivelist plugin:
   ```sh
   volatility -f <memory_image> --profile=<profile> hivelist
   ```
4. Record the virtual addresses of the hives and dump them to disk.
   ```sh
   volatility -f <memory_image> --profile=<profile> dumpregistry -o <virtual_address> -D <output_directory>
   ```
**Expected Output**: The Windows Registry hives are successfully extracted from the memory image and stored in the designated output directory for further analysis.

---

### Exercise 2: Analyzing the SAM Hive for User Account Details
**Objective**: Use Volatility to examine the SAM hive and retrieve user account data.

**Steps**:
1. Confirm that the SAM hive was successfully extracted from the memory image in Exercise 1.
2. Execute the following command to parse the SAM hive and extract account information:
   ```sh
   volatility -f <memory_image> --profile=<profile> hashdump -y <system_hive> -s <sam_hive>
   ```
**Expected Output**: User account information is displayed, including usernames and associated password hashes.

---

### Exercise 3: Investigating Autorun Entries in the Software Hive

**Objective**: Detect registry-based autorun entries that may indicate malicious persistence.

**Steps**:

1. Verify that the Software hive has been extracted from the memory image in Exercise 1.

2. Analyze autorun registry keys using the following command:
```sh
volatility -f <memory_image> --profile=<profile> printkey -o <software_hive_virtual_address> -K "Microsoft\Windows\CurrentVersion\Run"
```

**Expected Output**: Autorun entries from the Software hive are listed, highlighting any items that may represent potential persistence mechanisms.

---

### Exercise 4: Examining User Assist Keys in the NTUSER.DAT Hive

**Objective**: Review User Assist artifacts to identify recently executed applications for a specific user.

**Steps**:

1. Ensure the NTUSER.DAT hive has been extracted from the memory image in Exercise 1.

2. List User Assist entries using the following command:
```sh
volatility -f <memory_image> --profile=<profile> userassist -i
```

**Expected Output**: A list of recently accessed applications along with execution counts is displayed, aiding in the identification of suspicious user activity.

---

### Exercise 5: Correlating Registry Artifacts for Holistic Analysis

**Objective**: Correlate findings across multiple registry hives to assess potential malicious behavior.

**Steps**:

1. Review data gathered from earlier exercises, including user account details, autorun entries, and User Assist artifacts.

2. Identify patterns or anomalies that may suggest a security incident.

3. Document observations and outline recommendations for additional investigation or remediation.

**Expected Output**: Correlated registry artifacts provide a comprehensive view of suspected malicious activity, supported by evidence collected from multiple Windows Registry sources.

By completing these exercises, I gained hands on experience analyzing Windows Registry artifacts using Volatility. This work strengthened my memory forensics skills and improved my ability to identify persistence mechanisms and indicators of compromise during security investigations.
