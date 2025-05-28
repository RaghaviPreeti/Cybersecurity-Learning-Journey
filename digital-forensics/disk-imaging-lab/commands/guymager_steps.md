# Guymager – Forensic Imaging (GUI Workflow)

## Imaging Steps
1. Open Terminal:
   ```bash
   sudo guymager
   ```
2. Authenticate using the password
3. In Guymager:
   - Go to `Devices → Add special device`
   - Navigate to `filepath` and open it
   - Right-click the device → `Acquire Image`
4. Configure acquisition:
   - Format: **Expert Witness Format (EWF)**
   - Destination: `path to the desired storage location`
   - Filename: `descriptive name for the image file`
   - Check:
     - ✅ Calculate MD5
     - ✅ Calculate SHA-1
     - ✅ Re-read source
     - ✅ Verify image
5. Click **Start** to begin acquisition

## Validation
- Check `destination_path` for:
  - `.E01` image file
  - `.info` file with matching MD5 & SHA-1 hashes

  <div align="center">

--- 🔹🔹🔹 End of Section 🔹🔹🔹 ---

</div>
