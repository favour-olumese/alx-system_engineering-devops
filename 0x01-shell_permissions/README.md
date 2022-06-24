# Shell Permissions
`0-iam_betty` - Script to switch the current user to another user named `betty`.

`1-who_am_1` - Script that prints the effective username of the current user.

`2-groupas` - Script that prints all the groups that the current user belongs.

`3-new_owner` - Script that changes the owner of a file called `hello` to the user "betty."

`4-empty` - Script that create an empty file called `hello`.

`5-execute` - Script that adds execute permission to the onwer of the file `hello`.

`6-multiple_permissions` - Script that adds execute permission to the owner and the group owner, and read permission to other users, to the file `hello`.

`7-everybody` - Script that adds execution permission to the owner, the group owner and the other users, to a file name `hello`.

`8-James_Bond` - Script that sets the permission to the file `hello` as follows:

* Owner: no permission at all
* Group: no permission at all
* Other users: all the permissions

`9-John_Doe` - Script that sets the mode of the file `hello` in current working directory to -rwxr-x-wx.

`10-mirror_permissions` - Script that sets the mode of the file `hello` to have same mode as another file called `olleh`.

`11-directories_permissions` - Script that adds execute permission to all subdirectories of the current directory for the owner, the group owner and all other users. Regular files are not be changed.

`12-directory_permissions` - Script that creates a directory called `my_dir` with permissions 751 in the working directory.

`13-change_group` - Script that changes the group owner to `school` for the file `hello`.

`100-change_owner_and_group` - Script that changes the owner to `vincent` and the group owner to `staff` for all the files and directories in the working directory.

`101-symbolic_link_permissions` - Script that changes the owner and the group owner of `_hello` to `vincent` and `staff` respectively.

`102-if_only` - Script that changes the owner of the file `hello` to `betty` only if it is owned by the user `guillaume`

`103-Star_Wars` - Script that will play the StarWars IV episode in the terminal.

## Discussion
chmod - to change mode of file/directory.  
chown - to onwership of file/directory.
### File modes
| Octal Value | File Mode |
|------------|------------|
| 0 | --- |
| 1 | --x |
| 2 | -w- |
| 3 | -wx |
| 4 | r-- |
| 5 | r-x |
| 6 | rw- |
| 7 | rwx |

r implies read.
w implies write.
x implies execute.

-rw-r--r--: The first - shows that this is a file.
drwxr-xr-x: d shows that this is a directory.
lrw-r--r--: l shows that this is a symbolic link.

### Chmod symbolic notation
| Symbol | Meaning |
|--------|---------|
| u | File/directory owner |
| g | Group owner |
| o | Others/world |
| a | All (ugo) |

### Switching to another user
```shell
su <user_name>
```

### Printing effective username of the current user
```shell
whoami
```

### Printing all groups current user is part of
```shell
groups
```

### Change file owner
```shell
chown <new_owner> <file_name>
```

### Creating an empty file
```shell
touch <file_name>
```

### Adding execute permission to file owner
```shell
chmod u+x <file_name>
```

### Multiple permissions
Adding execute permission to the owner and the group owner, and read permission to other users.
```shell
chmod 754 <file_name>
```

### Adding execute permission to all file users
```shell
chmod a+x <file_name>
```
or
```shell
chmod +x <file_name>
```
or
```shell
chmod ugo+x <file_name>
```

### Give only other users full permission whilst stripping onwer and groups of permission
```shell
chmod 007 <file_name>
```

### Setting the mode of a file to -rwxr-x-wx
```shell
chmod 753 <file_name>
```

### Make a file have same mode as another file
```shell
chmod --refrence=<reference_file_name> <file_to_be_changed_name>
```

### Adding execute permission to all subdirectories for all users, whilst leaving regular files unchanged
```shell
sudo chmod +x $(find -type d)
```

### Creating a directory with permission 751
```shell
mkdir -m 751 <file_name>
```
-m implies mode

### Changing group owner of a file
```shell
chown :<group_name> <file_name>
```

### Changing owner and group owner for all files and subdirectories
```shell
chown -R <owner_name>:<group_name> .
```
-R implies recursively

### Changing owner and group owner of symbolic link
```shell
chown -h <owner_name>:<group_name> <symbolic_link>
```

### Changing the owner of a file if it is owned by a specific user
```shell
chown --from=<user_name_to_check> <new_owner>
```

### Watching starwars IV in the terminal
```shell
telnet towel.blinkenlights.nl
```
