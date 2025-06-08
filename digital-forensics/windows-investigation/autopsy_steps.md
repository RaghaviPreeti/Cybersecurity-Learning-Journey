# Autopsy Analysis Steps – Windows Investigation (Lab 04)

This document outlines the step-by-step process used to analyze a Windows forensic image using Autopsy.

---

## 🔍 Step-by-Step Forensic Procedure

### 1. Launch Autopsy

- Open a terminal and run the following command:

```bash
autopsy
```

<div align="center">

----- [ Section Break ] -----

</div>

### 2. Create a New Case

- Click on **“Create New Case”**.
- Fill in the case details:
  - **Case Name:** AngelaHousingInvestigation
  - **Base Directory:** Choose a folder to store your case data
  - Add any notes you’d like for the investigation.

<div align="center">

----- [ Section Break ] -----

</div>

### 3. Add Data Source

- Select **“Add Data Source”**.
- Choose **Disk Image or VM File**.
- Browse to select the `.E01` image file.
- Ensure **read-only mode** is selected to preserve evidence integrity.

<div align="center">

----- [ Section Break ] -----

</div>

### 4. Configure Ingest Modules

Check the following modules before starting the ingest process:

- File Type Identification
- Recent Activity
- Internet History
- Keyword Search
- Email Parser
- Metadata Extractor
- Executable File Analysis
- EXIF Parser

Click **“Next”** or **“Finish”** to begin analysis.

<div align="center">

----- [ Section Break ] -----

</div>

### 5. Analyze Artifacts

- Use the left-side tree structure to navigate key directories.
- Check:
  - File metadata (created/modified/accessed times)
  - Email content and headers
  - Installed programs and configuration files
  - Presence of scripts (e.g., `stego.py`)
  - Any signs of non-business applications (e.g., Steam, Discord)
  - Browser history and search artifacts

<div align="center">

----- [ Section Break ] -----

</div>

### 6. Document Key Evidence

For each piece of evidence:

- Note the **file path**, **timestamps**, and **relevance**.
- Take screenshots (internal use only) to support your findings.
- Build a **timeline of events** using timestamps from emails and files.

<div align="center">

----- [ Section Break ] -----

</div>

### 7. Close the Case

- Once analysis is complete, export or save any notes.
- Close the case properly within Autopsy to ensure all data is saved.
- Shut down Autopsy and close the browser tab.

> **Note:** All analysis was performed in read-only mode to maintain forensic soundness. Chain of custody was preserved throughout the process.

<div align="center">

--- 🔹🔹🔹 End of Section 🔹🔹🔹 ---

</div>

