# Getting Started With The Command line

 
 Computers are just machines that only understand 0s and 1s. So then how come you can do things on your computer through a nifty graphical user interface (GUI) - how come you can use your mouse to open programs and do things and instead of having to type in a series of 0s and 1s?

The answer lies in the various layers of abstraction that exist between the binary zeros and ones and the GUIs. These layers translate our interactions into instructions that the computer's hardware can execute. Among these layers, one of the most pivotal is the command line interface (CLI).

The Command Line Interface (CLI) is a text-based platform through which users input commands directly into a terminal, offering a more straightforward path to the computer's operating system compared to the graphical user interfaces (GUIs) most are familiar with. The CLI might initially appear less approachable than the GUI's visual navigation, but it grants users significantly greater control over their computer's operations.

Unlike the GUI, which simplifies interaction by visualizing the computer's file system and applications, the CLI demands an understanding of specific commands. This requirement, though it may seem like a barrier, is actually a gateway to more efficient computer use. Through the CLI, tasks that might take several steps in a GUI can often be executed swiftly with a single command.

The list of commands you can run will depend entirely on your operating system, and commands from one OS to the next may be widely different (think windows vs linux).

This tutorial will highlight some basic and useful command for the [Windows command prompt](#windows-command-prompt), as well as some [linux commands](#linux).


## How To Open The Command Prompt

1. Type cmd in the windows search bar and then click open.
2. Do the same steps as in 1. , but click pin to task bar. This will allow you to click on the command prompt to open it really quickly.
<figure align="center">
    <img src="../../../imgs/Command Prompt On The Task Bar.png" width="100%">
  <figcaption>Command Prompt On The Task Bar</figcaption>
</figure>

3. Navigate to anywhere you want in the file explorer, and in the top search bar, click on it and type in cmd.
<figure align="center">
    <img src="../../../imgs/Command Prompt From File Explorer.png" width="100%">
  <figcaption>Command Prompt From File Explorer</figcaption>
</figure> 


## Windows Command Prompt

> **Note:**
> 
> All file and folder paths in the commands use relative paths, so the path is relative to your current location.

- **`cd`**: Outputs your current path.
- **`cd {folder_name}`**: Navigates to the specified folder.
- **`cd ..`**: Navigates back one folder.
- **`dir`**: Outputs all files and folders in your current directory.
- **`del {file_name}`**: Deletes the specified file.
- **`rmdir {folder_name}`**: Deletes the specified folder. The folder must be empty.
- **`rmdir /S {folder_name}`**: Deletes the specified folder and everything in it.
- **`mkdir {folder_name}`**: Creates a new folder with the specified name.
- **`more {file_name}`**: Outputs the content of the specified file.
- **`move {original_location} {target_location}`**: Moves a file to a new location (can also be used to rename a file).
- **`ren "old_name" "new_name"`**: Renames a file.
- **`set`**: Lists all environment variables.
- **`set varName=varValue`**: Sets a new environment variable.
- **`fc {file_1} {file_2}`**: Shows the difference between two files.
- **`start .`**: Opens a new File Explorer window at the current file path.
- **`for /f "skip=9 tokens=1,2 delims=:" %i in ('netsh wlan show profiles') do @echo %j | findstr -i -v echo | netsh wlan show profiles %j key=clear`**: Shows all Wi-Fi passwords saved on your computer.
- **`code .`**: Opens Visual Studio Code at your current location.
- **`code`**: Opens Visual Studio Code with no files or directories open.

You can find a list of all available commands [here](https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/cd).

## Linux



> **Note:**
> 
> All file and directory paths in the commands use relative paths unless specified otherwise, making the path relative to your current location.

- **`pwd`**: Prints the current directory path.
- **`cd {directory_name}`**: Changes the current directory to the specified directory.
- **`cd ..`**: Moves up one directory level.
- **`ls`**: Lists all files and directories in the current directory.
- **`man {command}`**: Displays the manual page for the specified command, providing detailed information on its usage.
- **`rm {file_name}`**: Deletes the specified file.
- **`rmdir {directory_name}`**: Deletes the specified directory. The directory must be empty.
- **`rm -r {directory_name}`**: Deletes the specified directory and all of its contents.
- **`mkdir {directory_name}`**: Creates a new directory with the specified name.
- **`cat {file_name}`**: Displays the content of the specified file.
- **`mv {source} {destination}`**: Moves or renames a file or directory.
- **`cp {source} {destination}`**: Copies a file or directory.
- **`echo "text"`**: Displays the specified text.
- **`export VARIABLE_NAME=value`**: Sets a new environment variable.
- **`grep "text" {file_name}`**: Searches for the specified text within a file.
- **`find {directory} -name {file_name}`**: Searches for files within a directory hierarchy.
- **`chmod {permissions} {file_name}`**: Changes the permissions of a file or directory.
- **`sudo {command}`**: Executes a command with superuser privileges.
- **`apt-get install {package_name}`**: Installs a new package (Debian-based systems).
- **`nano {file_name}`**: Opens the specified file in the nano text editor.
- **`vi {file_name}`**: Opens the specified file in the vi text editor.
  - Use neovim, don't be weak!
- **`top`**: Displays running processes and their system resource usage.
- **`ps`**: Displays currently running processes.
- **`kill {process_id}`**: Terminates the specified process.

For a full list of all core Linux commands, [check out this page](https://ss64.com/bash/).

> **Note**
>
> Different linux distros will have their own unique commands. These are more specific to package management, system services, config tools, etc. The core linux commands will more than always likely be the same across all distros.

## Understanding Flags, Arguments, and Command Chaining

Commands in both Windows Command Prompt and Linux terminals are not just standalone instructions; they can be modified and extended through the use of flags and arguments. Additionally, multiple commands can be chained together to perform complex tasks efficiently. Understanding these concepts is crucial for leveraging the full power of the command line.

### Flags and Arguments

**Flags** (also known as options or switches) modify the behavior of a command. Flags usually precede arguments and are prefixed with a hyphen (`-`) in Linux and a slash (`/`) in Windows Command Prompt. They can control the output's detail level, set specific operation modes, or alter the command's default behavior.


- **Linux Example**: `ls -l /home` lists the contents of the `/home` directory in long format, showing detailed information.
- **Command Prompt Example**: `dir /B` lists the files and directories in the current directory in a bare format, showing only names.

**Arguments** are the targets or inputs for commands, such as filenames, user names, or paths. They tell the command what resource to act upon.

- **Linux Example**: In `cp file1.txt file2.txt`, `file1.txt` and `file2.txt` are arguments specifying the source and destination of the copy operation.
- **Command Prompt Example**: In `move file1.txt D:\Documents\`, `file1.txt` and `D:\Documents\` are arguments specifying the file to move and the destination folder.
  
In general commands (both on Linux & command Command Prompt) have the following general structure:

```Bash
command [options/flags] [arguments]
```

### Command Chaining

Both environments allow for **command chaining**, where the output of one command serves as the input to another, or commands are executed sequentially. This allows for powerful one-liners that can perform complex operations.

- **Linux**: Commands can be chained using pipes (`|`), allowing the output of one command to be passed as input to another. Logical operators such as `&&` (execute the next command if the previous succeeded) and `;` (execute commands sequentially regardless of success) are also used.
  - Example: `grep 'pattern' file.txt | wc -l` counts the number of lines in `file.txt` that match 'pattern'.

- **Command Prompt**: Similar to Linux, Command Prompt uses the pipe (`|`) and the `&&` operator. The `&` operator is used to execute commands sequentially regardless of success.
  - Example: `dir /B | findstr "example"` lists files and directories that contain "example" in their names.
