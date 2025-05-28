# Disk Imaging & Hashing – Digital Forensics Lab

## Objective
This lab focused on using both GUI and command-line tools to perform forensic imaging, hash validation, and integrity verification. Tools included **Guymager** and **dc3dd**, simulating real-world procedures for acquiring digital evidence from storage media.

<div align="center">

----- [ Section Break ] -----

</div>

## Tools Used
- **Guymager** – GUI-based imaging tool supporting raw (dd) and Expert Witness Format (EWF)
- **dc3dd** – CLI-based forensic imaging tool with integrated hashing and logging

<div align="center">

----- [ Section Break ] -----

</div>

## Key Activities

### Using Guymager
- Imported and acquired a disk image from a sample `.txt` file
- Compared dd vs EWF formats
- Verified MD5 and SHA-1 hashes post-acquisition
- Analyzed `.info` files for hash matching and file size validation

### Hashing Experiment
- Calculated MD5 hashes of files using `md5sum`
- Renamed and edited files to observe how hashes changed
- Reinforced the concept that even small changes result in different hashes

### Raw Acquisition & Verification
- Created a new disk image using `dd`
- Verified hash values post-acquisition
- Observed the impact of format choice on forensic workflows

### CLI Imaging with dc3dd
- Used `dc3dd` to image a removable device
- Generated MD5 hash during acquisition
- Saved logs with operational details and hash output

## Forensic Concepts Reinforced
- Role of hashing in ensuring evidence integrity
- Importance of not mounting drives during imaging
- Comparison of GUI and CLI workflows in forensic tasks

<div align="center">

----- [ Section Break ] -----

</div>

## Conclusion
This lab strengthened core digital forensics skills by combining GUI and CLI imaging tools, reinforcing the importance of careful acquisition and validation in evidence handling.

<div align="center">

--- 🔹🔹🔹 End of Section 🔹🔹🔹 ---

</div>
