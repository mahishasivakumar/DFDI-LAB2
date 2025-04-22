# EXP 2 : ANALYSIS THE DISK STRUCTURE USING SLEUTH KIT

## AIM:
To analyze the internal disk structure of a disk image using Sleuth Kit tools and identify file system metadata, directory structure, and other forensic details for digital investigation purposes.

## EQUIPMENT REQUIRED:
  ●	Hardware: Personal Computer (PC)

```
Register Number: 212222040095
Name: Mahisha S
```

## DESIGN STEPS:
### Step 1:

Obtain or create a disk image file (e.g., mahishadiskfile.iso) to analyze. 

### Step 2:
Use Sleuth Kit tools like istat, fsstat, and fls to examine the partition layout, file system details, and file listing.

### Step 3:
Interpret the output of the tools to understand the disk structure, including partitions, sectors, and files.

## PROGRAM:
Sleuth Kit Disk Analysis Commands
## PRELIMINARY STEP:
### Step1:

  ●	Run command prompt as administrator
  
  ![Screenshot 2025-04-22 211210](https://github.com/user-attachments/assets/ac78c759-fe87-4fb8-b2ee-24bfcd5a9191)



### Step2:

  ●	Verify Sleuthkit is installed.
  
  ![Screenshot 2025-04-22 202558](https://github.com/user-attachments/assets/0c233c6f-c652-48d9-b34d-0f6a9cdf871c)


### Step3:

  ●	Navigate to the binary file of Sleuthkit in command prompt:
  
  ![Screenshot 2025-04-22 203525](https://github.com/user-attachments/assets/5e6e2f41-ed6d-45f4-b4a9-e42e90dc8d36)


## PROCEDURE:
## ANALYSE THE FILE USING SLEUTHKIT TOOL:

### 1. View File Metadata
  ●	Use istat to view metadata of a file/directory using its inode number 0:
  
  ●	Command:  istat.exe -f filetype “file path” <inode number>
  
  ![Screenshot 2025-04-22 203735](https://github.com/user-attachments/assets/ac0d4c9d-3c45-4f8a-b857-2afe6e5ba371)

  #### OUTPUT SUMMARY:
  ●	Type: Directory
  
  ●	Permissions: dr-xr-xr-x (read + execute for all)
  
  ●	Created On: 2025-04-14 12:43:12 IST
  
  ●	Size: 2048 bytes, Sectors Used: 31

  
### 2. View Metadata of Inode 1

  ●	Use istat to view metadata of a file/directory using its inode number 1:
  
  ●	Command:  istat.exe -f filetype “file path” <inode number>
  
  ![Screenshot 2025-04-22 203804](https://github.com/user-attachments/assets/60357a8b-e961-4d21-a518-0d3eafd0b2f3)


  #### OUTPUT SUMMARY:
  
  ●	Type: Directory (metasploitable-linux-2.0.0)
  
  ●	Permissions: dr-xr-xr-x (read + execute for all)
  
  ●	Created On: 2 2025-03-11 19:34:00 IST
  
  ●	Size: 2048 bytes, Sectors Used: 32
  
### 3. View Metadata of Inode 6

  ●	Use istat to view metadata of a file/directory using its inode number 6:
  
  ●	Command:  istat.exe -f filetype “file path” <inode number>
  
  ![Screenshot 2025-04-22 203841](https://github.com/user-attachments/assets/a81d77dd-58b2-4d44-8ee7-778635421997)


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
  
  ![Screenshot 2025-04-22 203939](https://github.com/user-attachments/assets/8fb8c76d-493e-4c74-b148-0373bfa97e87)

  ![Screenshot 2025-04-22 203958](https://github.com/user-attachments/assets/71a93a44-d254-4279-bd4c-e5d892527e2c)


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
  
  ![Screenshot 2025-04-22 204117](https://github.com/user-attachments/assets/b0293036-4bf9-49ee-ab2b-79239db478aa)
  ![Screenshot 2025-04-22 204137](https://github.com/user-attachments/assets/84974457-d8e9-43b3-a5b5-50f68df60d39)



  
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
  ![Screenshot 2025-04-22 204344](https://github.com/user-attachments/assets/40ae6cf7-d6be-4939-80f5-a190a774152c)



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
  ![Screenshot 2025-04-22 204435](https://github.com/user-attachments/assets/cb7b5e15-b0f6-4660-a94e-e0a50349fda8)


  #### OUTPUT SUMMARY:
  •	Image Type: raw
  
  •	Size in Bytes: 1925926912 (approx. 1.79 GB)
  
  •	Sector Size: 512 bytes
  
  •	Confirms that the input image is a raw format disk image with standard sector configuration.


## RESULT:
Using The Sleuth Kit, the disk structure was successfully analyzed. 

