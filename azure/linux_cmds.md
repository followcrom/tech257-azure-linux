# Linux Commands Overview

Common Linux commands that are useful for managing and interacting with Linux-based systems.

### ls -l
Lists files and directories in the current directory with detailed information like permissions, number of links, owner, group, size, and timestamp.

`ls -l`

### cd
Changes the current directory to the specified directory.

`cd /path/to/directory`

### exit
Exits the current shell session.

`exit`

### cat
Displays the content of a file or concatenates multiple files.

`cat filename.txt`

### history
Shows a list of commands previously entered in the current session.

`history`

### curl
Transfers data from or to a server, supporting various protocols like HTTP, HTTPS, FTP.

`curl https://example.com`

### rm
Removes a file. Be cautious as this deletes the file permanently.

`rm filename.txt`

### nano
Opens the Nano text editor for creating or editing files.

`nano filename.txt`

### tree
Displays a tree representation of directory structure. May need to be installed.

`tree /path/to/directory`

### apt
Package management utility for Ubuntu/Debian, used to install, update, and remove packages.

`sudo apt update`

### sudo su
Switches to the root user, giving superuser access.

`sudo su`

### mv
Moves or renames a file or directory.

`mv oldname.txt newname.txt`


### rm
Removes a file. Be cautious as this deletes the file permanently.

`rm -filename.txt`

### rm -f
Forcefully removes a file, bypassing prompts. Be cautious as this deletes the file permanently.

`rm -f filename.txt`

### rm -r
Recursively removes a directory and its contents. Be cautious as this deletes the dir and its contents permanently.

`rm -r directory`

### mkdir
Creates a new directory.

`mkdir new_directory`

### touch
Creates a new file if it doesn't exist or updates the timestamp of an existing file.

`touch newfile.txt`

### file
Determines the type of a file.

`file filename.txt`

### cp
Copies files or directories.

`cp source.txt destination.txt`

### tab
Pressing the Tab key in the shell will auto-complete commands or show suggestions, including root directories when appropriate.

### cd /
Changes the current directory to the root directory.

`cd /`

### cd
Changes the current directory to the home directory.

`cd`

### tab at root

Pressing the Tab key at the root directory will show a list of root directories.

### pwd
Prints the current working directory.

`pwd`

# Env vars
Print all env vars:

```printenv```

Print one env var:

```printenv VARIABLE_NAME```


### Save an env var:

```export MYNAME=Richard```

```printenv MYNAME```

**Note:** This will not survice after you close the terminal.

### Save a persistant env var:

Modify .bashrc:

```nano .bashrc```

add to end of file:

```export MYNAME=Richard```

You can use the environment variables set in .bashrc without restarting your terminal. To apply the changes made to .bashrc, you can source the file. Sourcing .bashrc will execute the file's contents in the current shell session, updating your environment accordingly.

```source ~/.bashrc```


### Save a local var:

```VARNAME=var```

Print it:

```echo $VARNAME```

# Provisioning Nginx Script

### Step 1: Creating the Script

Create a new script file called `provision_nginx.sh` using your favorite text editor. For example:

`nano provision_nginx.sh`

```
#!/bin/bash

# Update the package repository
sudo apt update -y

# Upgrade the package repository
sudo apt update -y

# Install Nginx
sudo apt install -y nginx

# Start and enable Nginx to run on boot
sudo systemctl start nginx

# sudo systemctl is-enabled nginx

sudo systemctl enable nginx

sudo systemctl restart nginx

echo "Nginx has been installed and started."
```

Save and exit the text editor.

### Step 2: Making the Script Executable
Change the script's permissions to make it executable:

`chmod +x provision_nginx.sh`

### Step 3: Running the Script
Run the script to provision Nginx:

`./provision_nginx.sh`

The script will update the package list, install Nginx, start the Nginx service, and enable it to run at boot time. After execution, Nginx will be running on your server.

### Step 4: Verification
To verify Nginx is running, you can use the following command:


`systemctl status nginx`

Or, open a web browser and navigate to your server's IP address or domain. You should see the Nginx welcome page.


