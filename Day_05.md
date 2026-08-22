## Day 5 - Networking Commands, AWS EBS/LVM, Shell Scripting Basics

### Networking commands

```bash
nslookup google.com     # returns DNS + IP address
ping address            # checks online status, latency, packet loss
traceroute address      # shows packet path, finds delays/routing issues
dig google.com          # queries DNS directly, detailed DNS records
```

### Other tools

```bash
wget url        # downloads from the web
curl url        # used for API responses
ifconfig        # view/configure network interfaces
```

### Volumes - AWS EBS & LVM

```bash
lsblk           # list block devices (disks/storage)
df -h           # check disk usage, human-readable
```
- `xvda` = root volume name
- "Mounted on" = where volume is attached (`/` = root)

**Hierarchy:** Physical Volume → Volume Group → Logical Volume

```bash
pvcreate /dev/xvdf /dev/xvdg /dev/xvdh    # create physical volumes
pvs                                       # list physical volumes
vgcreate group_name pv1 pv2               # create volume group
vgs                                       # list volume groups
lvcreate -L 10G -n name vg_name           # create 10GB logical volume
lvs                                       # list logical volumes
```

**Mount a logical volume:**
```bash
mkdir /mnt/name
mkfs.ext4 path_of_lv
mount path_of_lv path_of_dir
```
attach = adds the block · mount = makes it visible

**Mount a disk directly (no LVM):**
```bash
mkdir /mnt/name
mkfs -t ext4 /dev/xvdh
mount /dev/xvdh /mnt/name
```

**Extend a logical volume:**
```bash
lvextend -L +5G path_of_lv
```

### Shell scripting basics

- shell = bash commands, script = sequence of commands, shell script = .sh file
- `#` = comment, `#!` = shebang, `#!/bin/bash` = declares shell in use
- `echo "hello"` - prints to screen

**Running a script:**
```bash
chmod 766 file_name
./file_name
```

**Example - create folder from script:**
```bash
mkdir -p folder_name   # -p avoids error if folder exists
```

**Variables:**
```bash
name="john"
echo $name
echo $USER   # environment variable
```

**Input from user:**
```bash
read -p "your name? " name
echo "your name is $name"
```

**Input from arguments:**
```bash
echo "your surname is $1"
# run as: ./file_name surname
# $0 = script name, $1 = first argument
```

### Next up
More shell scripting.
