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
Expected output:
```bash
paopao
```
2️⃣ Simulate a Disk Failure

This command marks /dev/sdb as failed in the RAID array.
```bash
sudo mdadm --manage /dev/md1 --fail /dev/sdb
```
3️⃣ Check RAID Status

View the current RAID status and verify if the disk is marked as failed.
```bash
cat /proc/mdstat
```
4️⃣ Verify Data Availability

Even if one disk fails, RAID 1 should still keep the data accessible.
```bash
cat /mnt/raid1/test.txt
```
Expected output:
```bash
paopao
```
5️⃣ Remove the Failed Disk

This command removes the failed disk from the RAID array.
```bash
sudo mdadm --manage /dev/md1 --remove /dev/sdb
```
6️⃣ Re-Add the Disk to RAID

This command adds /dev/sdb back into the RAID array for rebuilding.
```bash
sudo mdadm --manage /dev/md1 --add /dev/sdb
```
7️⃣ Check RAID Rebuild Status

Display detailed information about the RAID array and monitor the rebuilding process.
```bash
sudo mdadm --detail /dev/md1
```






