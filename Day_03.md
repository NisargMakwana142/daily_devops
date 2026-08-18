## Day 3 - SSH, EC2 Access, Users & Permissions

### SSH
- Runs on port 22
- Secure way to connect to and control a remote machine

### SSH keys
- Private key - stays local, used to prove identity
- Public key - placed on the server
- Private key connects to an EC2 instance holding the matching public key

### Connecting to EC2 from local shell
```bash
# 1. Locate the .pem file
# 2. Restrict permissions
chmod 400 "file.pem"

# 3. Connect
ssh -i "file.pem" user@public_dns_name
# -i = path to key, user = hostname, public_dns_name = instance DNS
```

### Connecting EC2 to EC2
```bash
# On source server
cd ~/.ssh
ssh-keygen                     # generates public + private key

# Copy public key contents into target server's
# ~/.ssh/authorized_keys

# From source server, connect using private key
ssh -i private_key_name username@public_IP_or_DNS
```

### Users & Groups
```bash
cat /etc/passwd                          # list all users
cat /etc/group                           # list all groups
sudo groupadd group_name                 # create a group
sudo gpasswd -M user1,user2 group_name   # -M = add multiple users
sudo usermod -aG group_name user_name    # -a append, -G group
```

### Permissions - `ls -l`
```
-rw-rw-r-- 1 username groupname size date filename   # file
drwxrwxr-x 2 username groupname size date foldername # directory
```

- First char: `-` = file, `d` = directory
- Next 9 chars in 3 groups of 3: owner / group / others
- `r` = read, `w` = write, `x` = execute

### Changing permissions & ownership
```bash
chmod 400 filename     # read-only
chown groupname filename
```

### grep
Global Regular Expression Print
```bash
grep -i "text to find" filename           # -i = case-insensitive
grep -i "text to find" filename | head    # first 10 lines (head -n 2 = first 2)
grep -i "text to find" filename | tail    # last 10 lines (tail -n 2 = last 2)
```

### Next up
Continuing Linux fundamentals, moving toward Git next.
