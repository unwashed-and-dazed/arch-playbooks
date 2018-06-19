## Install notes for Arch Linux
- Boot the Arch Linux ISO and get connected to the internet
- Initiate the ssh daemon with `# systemctl start sshd`
- Connect via SSH to the install ISO
- List the block devices with `# lsblk` and find your device. I'll assume /dev/sda as the install device
- Edit the disk with `# fdisk /dev/sda`
  - Entering sequentially the following commands will result in a EFI partition with 512MB and another partition for /
  1. g
  2. n
  3. (enter)
  4. (enter)
  5. +512M
  6. t
  7. 1
  8. n
  9. (enter)
  10. (enter)
  11. (enter)
  12. w

- Format the newly created partitions
  `# mkfs.fat -F32 /dev/sda1`
  `# mkfs.ext4 /dev/sda2`

- Mount the root partition on /mnt
