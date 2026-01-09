# Deleted File Recovery & Analysis Within Windows Environment

## Introduction
Files that appear to be deleted on Windows systems can still hold forensic value if they have not been fully overwritten. In this project, I focused on recovering deleted data and analyzing it to uncover evidence of user behavior or potential malicious activity. This lab walks through both file recovery and forensic analysis techniques commonly used during incident response and digital investigations.

## Lab Setup
To complete this project, I worked within a Windows operating system. The lab can be performed on either a physical host or a virtual machine using platforms such as VirtualBox or VMware.

### Pre-requisites
- Basic understanding of the Windows operating system
- Comfort using graphical and command-line tools
- Administrative access to the Windows machine

### Tools Used
The following tools were used during this project:
1. **Recuva** – for recovering deleted files
2. **FTK Imager** – for creating forensic disk images
3. **Autopsy** – for in-depth forensic analysis of disk images

#### Installing Recuva
1. Download Recuva from the official website: https://www.ccleaner.com/recuva  
2. Run the installer and complete the setup process.

#### Installing FTK Imager
1. Download FTK Imager from the AccessData website: https://accessdata.com/product-download  
2. Run the installer and follow the on-screen instructions.

#### Installing Autopsy
1. Download Autopsy from the official website: https://www.sleuthkit.org/autopsy/  
2. Run the installer and complete the installation.

---

## Exercises

### Exercise 1: Recovering Deleted Files with Recuva
**Objective**: Recover files that have been deleted from the Windows system.

**Steps**:
1. Launch Recuva.
2. Select the type of files to recover (for example, All Files).
3. Choose the location to scan, such as a specific drive or folder.
4. Start the scan and allow it to complete.
5. Review the list of recoverable files.
6. Select the files to restore and click `Recover`.
7. Choose a destination directory to save the recovered files.

**Expected Output**: Deleted files are successfully recovered and saved to a specified location.

---

### Exercise 2: Creating a Forensic Disk Image with FTK Imager
**Objective**: Preserve disk data by creating a forensic image for deeper analysis.

**Steps**:
1. Open FTK Imager.
2. Select `File` > `Create Disk Image`.
3. Choose the source type (for example, Physical Drive).
4. Select the target drive to image.
5. Follow the prompts to create an image file (such as E01 format) and save it to the desired location.

**Expected Output**: A forensic image of the selected disk is created and stored in the chosen directory.

---

### Exercise 3: Analyzing Deleted Files Using Autopsy
**Objective**: Examine deleted files contained within the forensic image.

**Steps**:
1. Launch Autopsy and create a new case.
2. Add the forensic image created in Exercise 2 as a data source.
3. Navigate to the `File Analysis` section.
4. Apply filters to display only deleted files.
5. Review and inspect the contents of the deleted files.

**Expected Output**: Deleted files are identified and their contents can be examined through Autopsy.

---

### Exercise 4: Examining Metadata of Recovered Files
**Objective**: Analyze file metadata to gain additional context about recovered data.

**Steps**:
1. In Autopsy, locate the recovered files.
2. Right-click a file and select `Extract File Metadata`.
3. Review metadata fields such as creation time, modification time, access time, file size, and file type.

**Expected Output**: Metadata details are displayed, providing insight into file history and usage.

---

### Exercise 5: Correlating Recovered Files with System Events
**Objective**: Understand why and when files were deleted by correlating them with system activity.

**Steps**:
1. In Autopsy, examine the system timeline around the deletion timeframe.
2. Identify relevant events such as file creation, modification, deletion, user logins, and application execution.
3. Correlate these events with the recovered files.
4. Document observations and note any suspicious or relevant activity.
5. Provide recommendations for additional investigation if necessary.

**Expected Output**: Recovered files are correlated with system events, offering a clearer picture of the circumstances surrounding their deletion.

---

## Outcome
By completing this project, I gained hands on experience recovering deleted files and performing forensic analysis on Windows systems. This lab strengthened my ability to preserve evidence, analyze recovered data, and correlate file activity with system events—core skills required for effective digital forensics and incident response investigations.

