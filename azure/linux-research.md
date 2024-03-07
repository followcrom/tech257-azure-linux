# Linux Research

1. [Managing File Ownership and Permissions](#managing-file-ownership-and-permissions)

2. [File Ownership and Permissions](#file-ownership-and-permissions)

3. [managing file permissions using numeric values](#managing file permissions using numeric values)


4. [changing file permissions](#changing file permissions)



# 1, Managing File Ownership and Permissions

## Managing file ownership
In Linux, every file and directory has an associated owner and group. The chown and chmod commands are commonly used to manage ownership and permissions, respectively.

### Viewing file ownership

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



# 2, File Ownership and Permissions

File permissions in Linux are divided into three categories: read (`r`), write (`w`), and execute (`x`), and these permissions can be independently set for the owner, the group, and others.

### Permissions for the User Entity in Linux

"User" entity refers to the file or directory's owner. These permissions include:

- **Read (`r`)**: The owner can view the contents of the file or list the contents of the directory.
- **Write (`w`)**: The owner can modify the file or add, remove, and rename files within the directory.
- **Execute (`x`)**: The owner can run the file as a program or script, or traverse the directory.


### Permissions for the Group Entity in Linux

"Group" entity refers to a specific group that is associated with the file or directory. The Group entity permissions include:

- **Read (`r`)**: Group members can view the contents of the file or list the contents of the directory.
- **Write (`w`)**: Group members can modify the file or add, remove, and rename files within the directory.
- **Execute (`x`)**: Group members can run the file as a program or script, or traverse the directory.

### Permissions for the Other Entity in Linux

"Other" entity refers to all users who are not the owner of the file or directory and are not members of the file's or directory's group. The permissions include:

- **Read (`r`)**: Allows viewing the contents of the file or listing the contents of the directory.
- **Write (`w`)**: Permits modifying the file or changing the contents of the directory (such as adding, removing, or renaming files within it).
- **Execute (`x`)**: Enables running the file as a program or script, or accessing the directory.

### Question

Given the scenario, the permissions you will have on this file are:

- **Read (`r`)**: You can view the contents of the file.

Since you are the owner and the User permissions are set to read-only, you will not have write or execute permissions on this file. Despite being the owner, the specific permissions set for the User entity (read-only in this case) determine your access level to the file.

### Description of File Permission Elements

The line `-rwxr-xr-- 1 tcboony staff 123 Nov 25 18:36 keeprunning.sh` provides detailed information about the file `keeprunning.sh`. Here's a breakdown of each element:

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


## managing file permissions using numeric values

// Your content for Topic 3 goes here...

## changing file permissions

// Your content for Topic 4 goes here...
