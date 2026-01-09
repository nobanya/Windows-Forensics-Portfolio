# Forensic Examination of Windows File System Artifacts

## Introduction
Windows file systems and operating system artifacts store a significant amount of forensic evidence that can be leveraged during security investigations. In this project, I focused on examining Windows file systems and extracting key artifacts using industry standard forensic tools. The goal of this lab is to identify, interpret, and correlate file system artifacts that may indicate suspicious or malicious activity.

## Lab Setup
For this project, I worked with a Windows operating system. The analysis can be performed on a physical system or within a virtual machine created using platforms such as VirtualBox or VMware.

### Pre-requisites
- Basic understanding of Windows operating system concepts
- Familiarity with command-line usage
- Administrative privileges on the Windows system

### Tools Used
The following tools were used throughout this project:
1. **FTK Imager** – for creating forensic disk images
2. **Autopsy** – a digital forensics platform built on The Sleuth Kit
3. **Windows File Analyzer** – for analyzing Windows-specific artifacts

#### Installing FTK Imager
1. Download FTK Imager from the AccessData website: https://accessdata.com/product-download  
2. Run the installer and complete the setup using the default options.

#### Installing Autopsy
1. Download Autopsy from the official website: https://www.sleuthkit.org/autopsy/  
2. Run the installer and follow the on-screen installation steps.

#### Installing Windows File Analyzer
1. Download Windows File Analyzer from the official site: http://www.mitec.cz/wfa.html  
2. Run the installer and complete the setup.

---

## Exercises

### Exercise 1: Creating a Forensic Disk Image with FTK Imager
**Objective**: Create a forensically sound image of a disk using FTK Imager.

**Steps**:
1. Launch FTK Imager.
2. Select `File` > `Create Disk Image`.
3. Choose the source type (for example, Physical Drive) and select the disk to be imaged.
4. Follow the prompts to create a forensic image (such as E01 format) and save it to a specified location.

**Expected Output**: A forensic image of the selected disk is successfully created and stored in the chosen destination.

---

### Exercise 2: File System Analysis Using Autopsy
**Objective**: Analyze the file system structure of the forensic image using Autopsy.

**Steps**:
1. Open Autopsy and create a new case.
2. Add the forensic image created in Exercise 1 as a data source.
3. Browse the file system hierarchy within Autopsy.
4. Examine important directories such as `Users`, `Program Files`, and `Windows`.

**Expected Output**: The file system structure is accessible, allowing identification and review of key directories and files.

---

### Exercise 3: Extracting and Analyzing the Master File Table (MFT)
**Objective**: Examine the Master File Table to identify file creation, modification, and deletion activity.

**Steps**:
1. Within Autopsy, locate the `$MFT` file under the NTFS file system.
2. Extract the `$MFT` file to the local system.
3. Parse the MFT using MFTECmd:
   ```sh
   MFTECmd.exe -f <path_to_MFT> -o <output_directory>
   ```
   
4. Review the parsed output to identify file activity timelines.

**Expected Output**: A parsed MFT output displaying file creation, modification, and deletion events.

---

### Exercise 4: Analyzing Windows Prefetch Files

**Objective**: Identify recently executed applications through Windows Prefetch artifacts.

**Steps**:

1. Open Windows File Analyzer.

2. Load Prefetch files extracted from the forensic image (typically located in C:\Windows\Prefetch).

3. Review execution data, including application names and run times.

**Expected Output**: A list of recently executed applications along with execution metadata.

---

### Exercise 5: Investigating User Activity Using Shellbags

**Objective**: Determine recently accessed folders and files through Shellbag artifacts.

**Steps**:

1. Use Autopsy to extract the NTUSER.DAT files for each user profile.

2. Analyze the extracted files with ShellBags Explorer:
```sh
SBECmd.exe -f <path_to_NTUSER.DAT> -o <output_directory>
```

3. Review the output to identify recently accessed directories and files.

**Expected Output**: Shellbag analysis reveals directory and file access history for each user.

---

### Outcome

By completing this project, I gained hands on experience performing forensic analysis on Windows file systems and artifacts. This lab strengthened my ability to create forensic images, analyze NTFS structures, and interpret key artifacts such as the MFT, Prefetch files, and Shellbags, skills that are essential for digital forensics, incident response, and security investigations.
