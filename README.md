# EXP 2 : ANALYSIS THE DISK STRUCTURE USING SLEUTH KIT

## AIM:
To analyze the internal disk structure of a disk image using Sleuth Kit tools and identify file system metadata, directory structure, and other forensic details for digital investigation purposes.

## EQUIPMENT REQUIRED:
  ●	Hardware: Personal Computer (PC)

```
Register Number: 212222040020
Name: Ashwinkumar S
```

## DESIGN STEPS:
### Step 1:

Obtain or create a disk image file (e.g., praveendisk.iso) to analyze. 

### Step 2:
Use Sleuth Kit tools like istat, fsstat, and fls to examine the partition layout, file system details, and file listing.

### Step 3:
Interpret the output of the tools to understand the disk structure, including partitions, sectors, and files.

## PROGRAM:
Sleuth Kit Disk Analysis Commands
## PRELIMINARY STEP:
### Step1:

  ●	Run command prompt as administrator
![Screenshot (195)](https://github.com/user-attachments/assets/d2ec88a3-c76c-49f5-a20b-4b9a67d80ab7)


### Step2:

  ●	Verify Sleuthkit is installed.
![Screenshot 2025-04-21 175410](https://github.com/user-attachments/assets/a61b9443-66a2-46b9-9034-868b7db94f7f)


### Step3:

  ●	Navigate to the binary file of Sleuthkit in command prompt: 
![image](https://github.com/user-attachments/assets/b10dbd6e-360e-4134-ae28-10f3ab45696d)


## PROCEDURE:
## ANALYSE THE FILE USING SLEUTHKIT TOOL:

### 1. View File Metadata
  ●	Use istat to view metadata of a file/directory using its inode number 0:
  
  ●	Command:  istat.exe -f filetype “file path” <inode number>
  
![image](https://github.com/user-attachments/assets/f415c356-b0cf-43a0-8b95-d677dc8f75c4)

  #### OUTPUT SUMMARY:
  ●	Type: Directory
  
  ●	Permissions: dr-xr-xr-x (read + execute for all)
  
  ●	Created On: 2025-04-14 12:43:12 IST
  
  ●	Size: 2048 bytes, Sectors Used: 31

  
### 2. View Metadata of Inode 1

  ●	Use istat to view metadata of a file/directory using its inode number 1:
  
  ●	Command:  istat.exe -f filetype “file path” <inode number>
  
 ![image](https://github.com/user-attachments/assets/b1a26d0f-05c9-4d66-ae0c-28b7395a0077)


  #### OUTPUT SUMMARY:
  
  ●	Type: Directory (metasploitable-linux-2.0.0)
  
  ●	Permissions: dr-xr-xr-x (read + execute for all)
  
  ●	Created On: 2 2025-03-11 19:34:00 IST
  
  ●	Size: 2048 bytes, Sectors Used: 32
  
### 3. View Metadata of Inode 6

  ●	Use istat to view metadata of a file/directory using its inode number 6:
  
  ●	Command:  istat.exe -f filetype “file path” <inode number>
  
 ![image](https://github.com/user-attachments/assets/2e6718c7-a152-4517-8216-f8ba4942997f)


  #### OUTPUT SUMMARY:
  
  ●	File Name: Metasploitable.vmx — This is a VMware configuration.
  
  ●	Type: File — It's a regular file, not a folder.
  
  ●	Permissions: -r-xr-xr-x — Read & execute allowed for everyone, no write access.
  
  ●	Created Time: 2025-03-11 19:34:16 IST — This is when the file was added to the ISO.
  
  ●	Size: 2804 bytes — Small file (just a few KB).
  
  ●	Sectors: 940391, 940392 — The disk sectors storing this file's content.

### 4. Analysis of Inode 6 Metadata via icat Utility

  ●	Use icat to extract file content using its inode number 6:
  
  ●	Command:  icat.exe -f filetype “file path” <inode number>
  
![image](https://github.com/user-attachments/assets/54963c75-19d0-4e80-8164-a3c8b9640fcf)
 ![image](https://github.com/user-attachments/assets/fda1fc66-6673-43e5-9ece-e0bdb735ea34)

  #### OUTPUT SUMMARY:
  The command retrieves the contents of a VMware virtual machine configuration file (Metasploitable.vmx). This file defines how the virtual machine is set up, including:
  
  ●	Hardware settings like CPU (numvcpus = "1"), RAM (memsize = "512"), and SCSI controller.
  
  ●	Networking options, with both NAT (ethernet0) and Host-only (ethernet1) adapters configured.
  
  ●	Storage devices, such as virtual hard disk (Metasploitable.vmdk) and CD-ROM (auto detect).
  
  ●	Additional devices like USB, EHCI, and multiple PCI bridges.
  
  ●	VM metadata, including UUID, display name (Metasploitable2-Linux), OS type (ubuntu), and annotations.
  
  ●	Security note: The annotation warns that this VM is intentionally vulnerable and should not be exposed to untrusted networks.

### 5. View File System Details Using fsstat
  ●	Use fsstat to view file system metadata of the ISO image.
  
  ●	Command:  fsstat -f filetype “file path”
 ![image](https://github.com/user-attachments/assets/d6d068e7-0479-4f85-a67d-a4c4e56496fa)
![image](https://github.com/user-attachments/assets/e0777b90-79ec-4994-bae0-348452f29882)

  
  #### OUTPUT SUMMARY:
  PRIMARY VOLUME DESCRIPTOR 1 File System Information:
  
  •	File System Type: ISO9660
  
  •	Volume Name: 14_04_2025
  
  •	Volume Set Size: 1
  
  •	Volume Set Sequence: 1
  
  •	Recording Application: AnyBurn
  
  Metadata Information:
  
  •	Path Table Location: 22–22
  
  •	Inode Range: 0 – 9
  
  •	Root Directory Block: 36827386058113052
  
  Content Information:
  
  •	Sector Size: 2048 bytes
  
  •	Block Size: 2048 bytes
  
  •	Total Sector Range: 0 – 940393
  
  •	Total Block Range: 0 – 940393

### 6.List Directory Structure

  ●	Use fls to view directory structure.
  
  ●	Command:  fls -f filetype -r  “file path”
 ![image](https://github.com/user-attachments/assets/7548eaa1-312a-4a4d-b43c-4138b92739f3)


  #### OUTPUT SUMMARY:
  
  •	Root Directory: metasploitable-linux-2.0.0 (Inode 1)
  
  •	Contained Files and Subdirectories:
  
  o	Metasploitable2-Linux/ — A directory (Inode 2)
  
  o	Metasploitable.nvram — NVRAM file storing BIOS settings (Inode 3)
  
  o	Metasploitable.vmdk — Virtual hard disk file (Inode 4)
  
  o	Metasploitable.vmsd — Snapshot metadata file (Inode 5)
  
  o	Metasploitable.vmx — Main configuration file (Inode 6)
  
  o	Metasploitable.vmxf — Extended configuration file (Inode 7)

### 7. Image File Information

  ●	Use img_stat – Sleuth Kit utility for viewing image file metadata.
  
  ●	Command:  img_stat  “file path”
 ![image](https://github.com/user-attachments/assets/3e50ddad-4fb7-4e61-be29-197bb1b5d276)


  #### OUTPUT SUMMARY:
  •	Image Type: raw
  
  •	Size in Bytes: 1925926912 (approx. 1.79 GB)
  
  •	Sector Size: 512 bytes
  
  •	Confirms that the input image is a raw format disk image with standard sector configuration.


## RESULT:
Using The Sleuth Kit, the disk structure was successfully analyzed. 

