## Install notes for Arch Linux
- Boot the Arch Linux ISO and get connected to the internet
- Initiate the ssh daemon with `# systemctl start sshd`
- Connect via SSH to the box
- List the block devices with `# lsblk` and find your device. I'll assume `/dev/sda` as the install device
- Edit the disk with `# fdisk /dev/sda`
  - _Issuing the following commands will result in a 512M EFI partition and a root partition with the remaining space_
  * g
  * n
  * (enter)
  * (enter)
  * +512M
  * t
  * 1
  * n
  * (enter)
  * (enter)
  * (enter)
  * w

- Format the newly created partitions

  `# mkfs.fat -F32 /dev/sda1`

  `# mkfs.ext4 /dev/sda2`

- Mount the root partition on /mnt with `# mount /dev/sda2 /mnt`

- Pacstrap the Arch system into /mnt with `# pacstrap -i /mnt base`
