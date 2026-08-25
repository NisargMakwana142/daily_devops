## Day 6 - Shell Scripting: Functions, Loops, Real Scripts

### $#
Returns number of arguments passed, excluding `$0` (script name).

### Multiline comments
```bash
<<text
comment
comment
text
```
Opening and closing word must match.

### Script: create a new user
```bash
#!/bin/bash

read -p "enter username " username
read -p "enter password " password

sudo useradd -m "$username"
echo -e "$password\n$password" | sudo passwd $username
```
- `read` - takes user input into a variable
- `-p` - shows a prompt message before input
- `-e` (on echo) - interprets `\n` as a newline, so the password is fed twice for `passwd`'s confirm step

### Script: install a package
```bash
#!/bin/bash

echo "Installing $1"
sudo apt-get update
sudo apt-get install $1
echo "Installation complete"
```

### Script: check if user exists
```bash
#!/bin/bash

read -p "enter username " username

count=$(cat /etc/passwd | grep $username | wc | awk '{print $1}')
if [ $count == 0 ]
then
    echo "user does not exist"
else
    echo "user exists"
fi
```
- `$(...)` stores a command's output in a variable
- `if` blocks close with `fi`

### Functions
```bash
#!/bin/bash

function create_file {
    read -p "enter file name " file_name
    touch $file_name
}
create_file
create_file
```

### Loops
```bash
#!/bin/bash

for (( num=1 ; num<=5 ; num++ ))
do
    echo "$num"
done
```
`do` blocks close with `done`.

### Script: backup a folder
```bash
#!/bin/bash

src=path_of_source_folder
des=path_of_destination_where_you_want_to_store_backup

timestamp=$(date '+%Y-%m-%d')
zip -r "$des/backup-$timestamp.zip" $src
```
Can be made dynamic by taking `src`/`des` as script arguments instead.

### Next up
Shell scripting done - Git and GitHub next.
