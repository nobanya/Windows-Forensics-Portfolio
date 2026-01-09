# Browser Artifact Extraction & Analysis on Windows Platform

## Introduction
Modern web browsers retain extensive records of user activity, including browsing history, cookies, cached content, saved credentials, and download information. In this project, I focused on extracting and analyzing browser artifacts from common Windows based browsers to reconstruct user activity and identify potential indicators relevant to forensic investigations. This lab demonstrates how browser data can serve as valuable evidence during security and incident response cases.

## Lab Setup
To complete this project, I used a Windows operating system. The analysis can be performed on a physical machine or within a virtual machine using platforms such as VirtualBox or VMware.

### Pre-requisites
- Basic understanding of the Windows operating system
- Familiarity with using command-line and desktop tools
- Administrative privileges on the Windows system

### Tools Used
The following tools were used during this project:
1. **WebBrowserPassView** – for extracting stored browser credentials
2. **BrowserHistoryViewer** – for reviewing browsing history across multiple browsers
3. **SQLite Database Browser** – for inspecting browser SQLite databases

#### Installing WebBrowserPassView
1. Download WebBrowserPassView from the NirSoft website: https://www.nirsoft.net/utils/web_browser_password.html  
2. Extract the downloaded ZIP archive to a directory of your choice.

#### Installing BrowserHistoryViewer
1. Download BrowserHistoryViewer from the Foxton Software website: https://www.foxtonsoftware.com/browser-history-viewer  
2. Run the installer and complete the installation process.

#### Installing SQLite Database Browser
1. Download SQLite Database Browser from the official website: https://sqlitebrowser.org/dl/  
2. Run the installer and follow the on-screen setup instructions.

---

## Exercises

### Exercise 1: Extracting Browser History
**Objective**: Extract and review browsing history from commonly used web browsers.

**Steps**:
1. Launch BrowserHistoryViewer.
2. Select the browsers to analyze (for example, Chrome, Firefox, or Edge).
3. Click `Load History` to extract browsing records.
4. Review the results, including visited URLs, timestamps, and visit frequency.

**Expected Output**: Browsing history from the selected browsers is displayed, showing visited websites along with corresponding dates and times.

---

### Exercise 2: Recovering Stored Browser Passwords
**Objective**: Identify credentials saved within web browsers.

**Steps**:
1. Open WebBrowserPassView.
2. Allow the tool to automatically scan supported browsers.
3. Review the output, which includes website names, usernames, and stored passwords.

**Expected Output**: A list of recovered browser credentials, including associated websites and user accounts.

---

### Exercise 3: Analyzing Browser Cookies
**Objective**: Examine browser cookies to understand user behavior and session-related data.

**Steps**:
1. Locate the cookies database for the browser being analyzed (for example, the `Cookies` file within the Chrome user data directory).
2. Open the cookies database using SQLite Database Browser.
3. Navigate to the `cookies` table and review stored entries such as host, cookie name, value, creation time, and expiration date.

**Expected Output**: Detailed cookie records that provide insight into user sessions, authentication tokens, and browsing behavior.

---

### Exercise 4: Examining Browser Cache
**Objective**: Analyze cached browser data to identify accessed web content and resources.

**Steps**:
1. Locate the cache directory for the selected browser (for example, the `Cache` folder in the Chrome user data directory).
2. Open BrowserHistoryViewer.
3. Select `File` > `Load Cache` and point to the browser’s cache directory.
4. Review cached entries, including URLs, cache types, and file sizes.

**Expected Output**: A list of cached web resources showing content accessed by the user.

---

### Exercise 5: Interpreting Download Records
**Objective**: Identify files downloaded by the user through the web browser.

**Steps**:
1. Locate the browser’s downloads database (for example, the `History` file in the Chrome user data directory).
2. Open the database using SQLite Database Browser.
3. Browse the `downloads` table to examine download details such as source URLs, file paths, and timestamps.

**Expected Output**: Download records revealing files obtained by the user, including when and where they were saved.

---

## Outcome
By completing this project, I gained hands on experience extracting and interpreting browser artifacts on Windows systems. This lab strengthened my ability to analyze browser history, credentials, cookies, cache data, and downloads—skills that are essential for digital forensics, incident response, and reconstructing user activity during investigations.

