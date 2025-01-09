# Interview-questions-for-devops

## Linux Folder Structure

The folder structure in Ubuntu Linux follows the Filesystem Hierarchy Standard (FHS), which is a standard for organizing the files and directories on a Unix-like operating system. Here is an overview of the main directories you will typically find in Ubuntu:

- **/bin**: Contains essential command-line executable files (binaries) that are available to all users.

- **/boot**: Contains files related to the boot process, including the Linux kernel, initial ramdisk (initrd), and bootloader configuration.

- **/dev**: Contains device files that represent and allow access to various hardware devices on the system.

- **/etc**: Contains system-wide configuration files for various applications and services.

- **/home**: The home directories for individual users. Each user typically has a subdirectory here to store their personal files and settings.

- **/lib** and **/lib64**: These directories contain shared libraries needed by the system and applications. The "lib64" directory is present on 64-bit systems.

- **/mnt**: A general-purpose mount point for temporarily mounting filesystems.

- **/opt**: Contains optional software packages installed on the system. Applications installed here are often self-contained in their own directories.

- **/proc**: A virtual filesystem that provides information about processes and system status. It is used by many system utilities to obtain runtime information.

- **/root**: The home directory for the root user, the administrative superuser.

- **/run**: A temporary filesystem that contains runtime data for various system services. It is cleared on each reboot.

- **/sbin**: Contains system binaries (executable files) that are primarily used by the root user for system administration tasks.

- **/srv**: Contains data for services provided by the system.

- **/tmp**: A directory for temporary files created by applications and users. Its contents are typically cleared on each reboot.

- **/usr**: Contains user-related programs, libraries, documentation, and shared resources. It has subdirectories such as /usr/bin for user binaries, /usr/lib for libraries, and /usr/share for shared data.

- **/var**: Contains variable data that changes during the system's operation, such as logs, databases, and spool files.

This is a high-level overview of the Ubuntu Linux folder structure. Each directory serves a specific purpose in organizing the system's files and resources.

## Important Linux Commands for DevOps Engineers

## Directories
- `/bin` => Absolute path containing user executable commands like `pwd`, `whoami`, etc.
- `/sbin` => Contains commands executable only by the root user.
- `/etc` => Configuration files.
- `/boot` => Contains the Linux kernel files.
- `/proc` => Contains system information.

## `ls` Command
- `ls /{particular directory}` => Relative path.
- `ls /opt/dev/devops/ansible` => Absolute path.
- `ls -lt` => Shows the latest timestamp.
- `ls -ltr` => Shows in reverse order.

---

# Vim Editor

- `i` => Insert mode.
- `:wq` => Save and exit.
- `o` => Goes one line down and starts in insert mode.
- `:se nu` => Shows line numbers.
- `Shift + g` => Goes to the last line.
- `gg` => Goes to the first line.
- `yy` => Copy the line.
- `p` => Paste below the current line.
- `P` => Paste above the current line.

---

# File Command

Used to check whether it is a file or binary:
- `-` : Regular file.
- `D` : Directory.
- `L` : Link file.
- `c` : Special file.
- `S` : Socket.
- `P` : Pipe.

## Creating Links

Why it is used: To access a file available at `/opt/devops/dev/commands/command.txt` easily.

```sh
ln -s /opt/devops/dev/commands/command.txt cmd
```
- `ln` : Command.
- `-s` : Soft link.
- `destination location` : ```/opt/devops/dev/commands/command.txt.```
- `source` : cmd.

## To remove the link
```unlink cmd```
## Grep Command
```grep <word name> <filename>
grep <word name> *
grep -R <word name> /etc
```
## Head Command
Displays the first 10 lines
```head <filename>
head -n 100 <filename> # Displays the first 100 lines
```
## Tail Command
Displays the last 10 lines
```tail <filename>
tail -n 100 <filename> # Displays the last 100 lines
tail -f <filename> # Shows dynamic content, useful for logs
```
## Find Command
``` find /etc -name host* ```
## Lsof Command
```lsof -u <username>``` # Identifies which user is logged in
## Editing Sudo Files
**visudo # Use this command to edit /etc/sudoers**

## Package Management
For RHEL-based systems:

- **List packages**
  ``` rpm -qa ```
- **Find architecture**
  ``` arch && uname -m ```
- **Download RPM-based function**
  ```curl <link of the application.rpm> -o <name of the application> ```
- **Install RPM-based application**
  ``` rpm -ivh <application name.rpm> ```
- **Uninstall using RPM command**
  ``` rpm -e <application name> ```
- **Fix path issues**
  ```
  echo 'export PATH=$PATH:/usr/local/bin' >> ~/.bashrc
  source ~/.bashrc
  ```
## Services
**To see if the service is in systemd:**
``` cat /etc/systemd/system/multi.user.target.wants/httpd.service ```
## Processes
**top command:**

- `0.00` => Current limit.
- `0.03` => Last 5 mins.
- `0.05` => Last 15 mins.
**ps aux => Check for processes.**

**Check all processes with their parent process ID: ps -ef**

## Kill process:
``` kill -9 PID # Forcefully stop process
   kill PID # Gracefully stop process, child processes also stopped
```

**Difference between Zombie & Orphan Process:**
- Orphan Process: A child process that remains running even after its parent process is terminated.
- Zombie Process: A process that has completed its task but still shows an entry in the process table.

## Archive
**To tar the folder or file**
``` tar -czvf <archive-filename.tar.gz> filename_or_directory_name ```
- `c` : Create.
- `z` : Compress.
- `v` : Verbose.
- `f` : File.

**To untar the file or folder:**

``` 
tar -xzvf <archive-filename.tar.gz>
```
```
tar -xzvf <archive-filename.tar.gz> -C /opt # Untar to a specific folder 
```
`x` : Unzip.

# Ubuntu Commands
- **Search for a file name**
  ``` dpkg -l | grep <application name> ```
- **Remove an application**
  ``` dpkg -r <application name> ```
- **Upgrade packages**
  ``` apt upgrade ```
- **delete all the contains package**
  ``` apt purge <package-name> ```
- **Temporarily set vim as the default editor**
  ```
  export EDITOR=vim
  ```
   
