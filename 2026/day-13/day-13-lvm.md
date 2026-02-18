# Day 13 – Linux Volume Management (LVM)
## Task 1: Check Current Storage
Run: lsblk, pvs, vgs, lvs, df -h
1. lsblk : list all block devices. <img width="1035" height="484" alt="image" src="https://github.com/user-attachments/assets/743cc0ee-c075-4c28-8616-08eb872b0c18" />

2. df -h : shows file system and disk space usage. <img width="1040" height="444" alt="image" src="https://github.com/user-attachments/assets/ecd622bd-ef4c-434e-9392-266cff507b69" />

3. pvs : list all physical volume in system. <img width="961" height="168" alt="image" src="https://github.com/user-attachments/assets/33cf41e9-6177-456b-b592-a952fbeea9ce" />

4. vgs : list volume groups in system. <img width="732" height="131" alt="image" src="https://github.com/user-attachments/assets/989e6658-d697-4029-8199-24aec6874b3b" />

5. lvs : list all logical volume in system. <img width="1415" height="142" alt="image" src="https://github.com/user-attachments/assets/2c06edbb-2fae-41e6-8b5a-b5e8ffbb4939" />

## Manage Virtual Disk (without have extra spare disk)

Step 1: Create a virtual disk file 
dd if=/dev/zero of=/tmp/disk1.img bs=1M count=1024  <img width="1090" height="216" alt="image" src="https://github.com/user-attachments/assets/a660d738-79e5-4617-8ea3-d6c2e823bea0" />

Step 2: Attach file as disk device
losetup -fP /tmp/disk1.img  <img width="1090" height="202" alt="image" src="https://github.com/user-attachments/assets/68bb6bff-4edd-4fd8-859e-bfcf36f4730a" />

Step 3: Check loop device
losetup -a <img width="1066" height="283" alt="image" src="https://github.com/user-attachments/assets/0f7252df-785c-4119-97dd-46d1799ff9da" />


Challenge Tasks
Step 1 : Create Physical Volume. pvcreate /dev/<disk_name> 
<img width="869" height="221" alt="image" src="https://github.com/user-attachments/assets/fcaf33cd-5e0c-4168-8fe4-32724a4e69ae" />

Step 2 : Create Volume Group. 
<img width="1090" height="220" alt="image" src="https://github.com/user-attachments/assets/a5dac998-8ae1-49c9-844c-40c3c877cf88" />
 
Step 3: Create Logical Volume 
<img width="1090" height="223" alt="image" src="https://github.com/user-attachments/assets/a8dafff5-8d34-4712-9c44-6ab372679313" />

Step 4: Format file system and Mount 
mkfs.ext4 /dev/devops-vg/app-data  <img width="1090" height="488" alt="image" src="https://github.com/user-attachments/assets/4b0dddf2-9d8a-4d2f-a0eb-cecb571dd113" />

mkdir -p /mnt/app-data  <img width="983" height="198" alt="image" src="https://github.com/user-attachments/assets/9882f637-8490-48a1-8144-5980f5bf64dd" />

mount /dev/devops-vg/app-data /mnt/app-data  <img width="1090" height="408" alt="image" src="https://github.com/user-attachments/assets/6f035aec-2e8c-4e64-9776-bfe650c00c40" />

df -h /mnt/app-data  <img width="1090" height="192" alt="image" src="https://github.com/user-attachments/assets/00b5f21f-dfb9-4493-a4c9-496b58154630" />

Step 5: Extend the Volume
lvextend -L +200M /dev/devops-vg/app-data  <img width="1090" height="157" alt="image" src="https://github.com/user-attachments/assets/50f57155-0258-42c8-bc1d-2b52fccebc08" />
 
resize2fs /dev/devops-vg/app-data  <img width="1090" height="654" alt="image" src="https://github.com/user-attachments/assets/fe0bcdb5-4e24-4c13-b7aa-fb105a394898" />

df -h /mnt/app-data  <img width="1090" height="146" alt="image" src="https://github.com/user-attachments/assets/6b4d2ac8-b0ff-4f02-b880-a41329b31353" />



