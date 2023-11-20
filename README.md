# public-docs

### Formatting External Drives, Flash Drives, Etc.

```bash
# to completely wipe a disk, get the device file (for example  /dev/sda)
sudo fdisk -l

# DELETE DATA # # # #
# securely purge all data: (Assuming /dev/sda is the device to reformat).
# DO NOT MIX UP "if" AND "of" parameters. dd is dangerous.
sudo dd if=/dev/zero of=/dev/sda

# OR just delete the partition using fdisk
sudo fdisk /dev/sda
# After starting the fdisk utility: run the "d" command to delete partitions

# CREATE NEW PARTITION # # # #
sudo fdisk /dev/sda
# After starting the fdisk utility: run the "g" command to create a gpt partition table.
# Run the "n" command to add a new partion.
#   Partition number 1 is ok (default)
#   use default first and last sector
# Run the "w" command to write changes to the disk

# Verify the partition is create and has the correct size
sudo fdisk /dev/sda -l

# SETUP FILESYSTEM (assuming the partition you just created is /dev/sda1)
sudo mkfs.ext4 /dev/sda1

# Done!, test it out
sudo mount /dev/sda1 /mnt
```