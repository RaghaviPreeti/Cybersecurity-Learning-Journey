# dc3dd – Command Line Imaging

## Step 1: Identify the Device
```bash
sudo fdisk -l
```
Look for your removable device (e.g., `/dev/sdb`).

## Step 2: Acquire Image with Logging & Hash
```bash
sudo dc3dd if=/dev/sdb of=/forensics/lab2image3.dd hash=md5 log=/forensics/lab2image3.txt
```

## Command Breakdown:
- `if=`: input file (source disk)
- `of=`: output file (forensic image)
- `hash=md5`: generates MD5 hash
- `log=`: stores output + hash details in a `.txt` file

## Step 3: Verify Image Hash

### Method 1:
```bash
md5sum /forensics/lab2image3.dd
```

### Method 2:
```bash
cat /forensics/lab2image3.txt
```

## Notes
- Never mount a suspect drive before imaging — it can modify data.
- `dc3dd` is useful in headless environments or when you need full control over hashing and logging.

<div align="center">

--- 🔹🔹🔹 End of Section 🔹🔹🔹 ---

</div>
