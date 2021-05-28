# Base installation

## Rank the mirrors before for faster downloads
📊 This will rank the mirrorlist. You may replace United States with your country
```bash
reflector -c 'United States' -a 15 -p https --sort rate --save /etc/pacman.d/mirrorlist
pacman -Syy
```

## Start the installation
⏳ This will install the system and may take a while
```bash
pacstrap /mnt base base-devel linux linux-firmware linux-lts sysfsutils usbutils e2fsprogs inetutils netctl nano less which man-db man-pages
```
::: warning
⚠️ To ensure system stability append the microcode package for your CPU
- `amd-ucode` for AMD CPUs
- `intel-ucode` for Intel CPUs 
- See <https://wiki.archlinux.org/index.php/Microcode>
:::

### Create filesystem table
This will create the file system table which contains all the partitions and mountpoints
```bash
genfstab -U /mnt >> /mnt/etc/fstab
```

### Change root
After you entered this command, you are basically in the installed system
```bash
arch-chroot /mnt
```
