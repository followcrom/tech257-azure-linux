# Linux Research

1. [Managing File Ownership](#managing-file-ownership)

2. [Managing File Permissions](#managing-file-permissions)

3. [Managing File Permissions Using Numeric Values](#managing-file-permissions-using-numeric-values)

<br>

# Managing File Ownership

## Managing file ownership
In Linux, every file and directory has an associated owner and group. The chown and chmod commands are commonly used to manage ownership and permissions, respectively.

## Viewing file ownership

Use the ls command with the -l (long listing) option. This command provides detailed information about files and directories, including their ownership.

```ls -l /path/to/file```

For directories, you can add the -d option to view the directory's own details rather than its contents:

```ls -ld /path/to/directory```


## Default Permissions

When a user creates a file or directory in Linux, the newly created file or directory belongs to the user who created it. When a user creates a new file in Linux, the default permissions usually do not include execute (`x`) permissions for the owner.

**Files**: Typically, files are created with the default permissions of 644 (rw-r--r--). This means the file owner has read and write permissions, while the group and others have read-only permissions.

**Directories**: Directories usually have the default permissions of 755 (rwxr-xr-x), allowing the owner to read, write, and execute (navigate) the directory. Group members and others can read and execute but cannot write to the directory.

The user can explicitly add execute permissions with:

`chmod +x filename`.

<br><br>

# Managing File Permissions

File permissions in Linux are divided into three categories: read (`r`), write (`w`), and execute (`x`), and these permissions can be independently set for the owner, the group, and others.

### Permissions for the User Entity

"User" refers to the file or directory's owner. These permissions include:

- **Read (`r`)**: The owner can view the contents of the file or list the contents of the directory.
- **Write (`w`)**: The owner can modify the file or add, remove, and rename files within the directory.
- **Execute (`x`)**: The owner can run the file as a program or script, or traverse the directory.


### Permissions for the Group Entity

"Group" entity refers to a specific group that is associated with the file or directory. The Group entity permissions include:

- **Read (`r`)**
- **Write (`w`)**
- **Execute (`x`)**

### Permissions for the Other Entity

"Other" entity refers to all users who are not the owner of the file or directory and are not members of the file's or directory's group. The permissions include:

- **Read (`r`)**
- **Write (`w`)**
- **Execute (`x`)**

### Question:
You give the following permissions to a [file: Use](file: Us "‌")r permissions are read-only, Group permissions are read and write, Other permissions are read, write and execute. You are logged in as the user which is owner of the file. What permissions will you have on this file? Explain.

Given the scenario, the permissions you will have on this file are:

- **Read (`r`)**: You can view the contents of the file.

### Description of File Permission Elements

The line `-rwxr-xr-- 1 tcboony staff 123 Nov 25 18:36 keeprunning.sh` provides detailed information about the file `keeprunning.sh`.

Here's a breakdown of each element:

- `-rwxr-xr--`: This is the file's permission string, where:
  - `-`: The first character indicates the file type. A dash (`-`) signifies a regular file.
  - `rwx`: The next three characters represent the owner's permissions. In this case, `rwx` means the owner (`tcboony`) has read (`r`), write (`w`), and execute (`x`) permissions.
  - `r-x`: The following three characters show the group's permissions. Here, `r-x` means the group (`staff`) has read (`r`) and execute (`x`) permissions but no write permission (`-`).
  - `r--`: The last three characters represent the permissions for others. `r--` indicates that others can read (`r`) the file but cannot write (`-`) or execute (`-`) it.

- `1`: This number shows the count of hard links to the file.

- `tcboony`: This is the username of the file's owner.

- `staff`: This represents the group associated with the file.

- `123`: This is the file size in bytes.

- `Nov 25 18:36`: This indicates the last modification date and time of the file.

- `keeprunning.sh`: This is the name of the file.

<br><br>

# Managing File Permissions Using Numeric Values

- Read (r) permission is `4`.
- Write (w) permission is `2`.
- Execute (x) permission is `1`.

Permissions are combined for each class of users (owner, group, and others) using the sum of these values. For example:

- To give the owner read and write permissions, you would use `6` (read + write, or 4+2).
- To give the group read and execute permissions, you would use `5` (read + execute, or 4+1).
- To give others only execute permission, you would use `1`.

A full permission set combines these values in a three-digit number, like `755`, which is a common setting for web files, allowing the owner full permissions and the group and others to read and execute.



So, `Read + Write + Execute = 4 + 2 + 1 = 7`.

- Owner: `7` (read + write + execute)
- Group: `4` (read)
- Others: `4` (read)

### 644 in Linux file permissions
The numeric mode 644 in Linux file permissions is quite common and has a specific meaning for the access it grants to the file for different user classes. Breaking it down:

- Owner: `6` (read + write)
- Group: `4` (read)
- Others: `4` (read)

<br>

# Changing File Permissions
To change file permissions in Linux, you use the **chmod (change mode)** command. The chmod command can be used with symbolic representations (like r, w, x for read, write, execute permissions) or numeric (octal) values that represent these permissions.

To change permissions on a file, the end user typically needs to be either:

- The owner of the file

- A privileged user: a user with superuser (root) privileges

### Examples of Changing File Permissions

#### 1, Set Initial Permissions
To set User to read, Group to read + write + execute, and Other to read and write only:

`chmod u=r,g=rwx,o=rw testfile.txt`

- u=r: Sets the User's permission to read only.

- g=rwx: Sets the Group's permissions to read, write, and execute.

- o=rw: Sets Others' permissions to read and write.

#### 2, Add Execute Permissions (to all entities)
To add execute permissions to all entities (User, Group, Other), you can use:

`chmod a+x testfile.txt`

- a+x adds execute permissions to all classes (user, group, others).

#### 3, Take Write Permissions Away from Group

`chmod g-w testfile.txt`

- g-w removes the write permission from the group.

#### 4, Use Numeric Values to Set Specific Permissions

`chmod 640 testfile.txt`

- 6 (User): Read + Write (4+2)

- 4 (Group): Read

- 0 (Other): No permissions