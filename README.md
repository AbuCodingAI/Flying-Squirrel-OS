╔═════════════════════════╗

║Flying Squirrel OS README           ║

║Every Command Reference                               ║

╚═════════════════════════╝

                    


🔧 RECOVERY TOOLS (Filesystem Repair)
──────────────────────────────────────

fixLinux <device>
  Repair ext4 filesystem
  Example: fixLinux /dev/sda1

fixWin <device>
  Repair NTFS filesystem
  Example: fixWin /dev/sda1

clone <source> <destination>
  Clone/backup disk or partition
  Example: clone /dev/sda /dev/sdb
  Example: clone /dev/sda /backup.img

grub-install <device>
  Repair GRUB bootloader (install to MBR)
  Example: grub-install /dev/sda

mount_drive <device> <mount_point>
  Mount filesystem (ext4, NTFS, FAT32)
  Example: mount_drive /dev/sda1 /mnt

unmount <mount_point>
  Unmount filesystem
  Example: unmount /mnt

/set <path>
  Change root (chroot) into mounted system
  Example: /set /mnt
  (All subsequent commands operate within chroot)

📁 NAVIGATION & FILES
──────────────────────────────────────

ls [path]
  List files and directories
  Example: ls
  Example: ls /mnt/home

cd <path>
  Change current directory
  Example: cd /mnt
  Example: cd ..

dump <file>
  View file contents (text or hex for binary)
  Example: dump /etc/fstab
  Example: dump /boot/grub/grub.cfg

r+w <file>
  Edit file (read+write mode)
  Example: r+w /etc/fstab
  Editor commands: i (insert), d (delete), w (write), q (quit)

💾 DISK & DRIVE OPERATIONS
──────────────────────────────────────

ls //
  List all disks and partitions
  Output shows disk size, partitions, filesystem types

dv check <device>
  Check disk health/SMART status
  Example: dv check /dev/sda

dv badblocks <device>
  Scan for bad sectors
  Example: dv badblocks /dev/sda

dv partition <device>
  Show partition table
  Example: dv partition /dev/sda

🖥️  SYSTEM COMMANDS
──────────────────────────────────────

help
  Show this command list
  Example: help

restart
  Reboot system immediately
  Example: restart
  (Gives 3-second countdown)

q
  Quit Flying Squirrel Bash / shutdown
  Example: q

🎯 COMMON RECOVERY SCENARIOS
──────────────────────────────────────


1️⃣  Repair broken Linux system:
   mount_drive /dev/sda1 /mnt
   /set /mnt
   fixLinux /dev/sda1
   q
   restart

2️⃣  Backup disk before repair:
   clone /dev/sda /backup.img
   mount_drive /dev/sda1 /mnt
   fixLinux /dev/sda1
   restart

3️⃣  Repair Windows NTFS:
   mount_drive /dev/sda1 /mnt
   fixWin /dev/sda1
   restart

4️⃣  Fix GRUB bootloader:
   grub-install /dev/sda
   restart

5️⃣  Browse broken system:
   mount_drive /dev/sda1 /mnt
   cd /mnt
   ls
   dump /etc/fstab
   cd /home
   ls

📋 PROMPT FORMAT
──────────────────────────────────────

squirrel[/current/path]#

Shows current directory after each cd command
Shows [chrooted] if /set is active

⚠️  ERROR MESSAGES
──────────────────────────────────────

All errors follow format:
ERROR: command failed — reason

Examples:
ERROR: fixLinux failed — Device not found: /dev/sdX1
ERROR: mount_drive failed — Already mounted
ERROR: fixWin failed — NTFS repair not supported

✨ SPECIAL FEATURES
──────────────────────────────────────

• Tab completion (partial, if enabled)
• Command history (arrow keys, if enabled)
• Persistent working directory (cd sticks)
• Supports absolute paths (/mnt/file) and relative (./file)
• Automatic error recovery (bad command doesn't crash shell)

🐿️  BOOT VERSIONS
──────────────────────────────────────

BIOS version:   squirrel-bios.iso (128KB) - MBR bootloader
UEFI version:   squirrel-uefi.iso (380KB) - UEFI bootloader
Both fit on a single 3.5" floppy disk!

##Flying Squirrel OS Recovery — Minimal. Fast. Reliable. 🐿️
═══════════════════════════════════════════════════════════════════
