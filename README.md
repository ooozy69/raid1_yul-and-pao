# Raid 1
This guide demonstrates how to test a RAID 1 setup using mdadm in Ubuntu/Linux.
It includes creating a test file, simulating a disk failure, removing the failed disk, re-adding it, and checking RAID recovery status.

📌 Test RAID 1
1️⃣ Create a Test File

This command creates a file named test.txt inside the RAID mount directory.
```bash
echo "paopao" | sudo tee /mnt/raid1/test.txt
```
Verify the File Content

Use cat to display the content of the file.
```bash
cat /mnt/raid1/test.txt
```
