---
title: "Essential Commands in Linux - File and System Management, Exploring Touch, LS, and More!"
seoTitle: "Essential Commands for File and System Management: Exploring Touch, LS"
seoDescription: "A Guide to Linux Basic Commands and file management operations like Touch, Timestamps, and Listing Files etc"
datePublished: Sat Jun 03 2023 14:53:01 GMT+0000 (Coordinated Universal Time)
cuid: clig45wqz000809mhfjfc9wkn
slug: essential-commands-in-linux-file-and-system-management-exploring-touch-ls-and-more
cover: https://cdn.hashnode.com/res/hashnode/image/stock/unsplash/4Mw7nkQDByk/upload/568f021b20b3be404b4a13ee04f90f0c.jpeg
tags: linux, linux-for-beginners, linux-basics, linux-commands

---

1. `pwd` (Print Working Directory): This command shows you the current directory you are in. It's like asking, "Where am I?" For example, if you're in the "Documents" folder, running `pwd` will display `"/home/user/Documents"` to let you know that you're currently in that directory.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1685698459781/bf063be8-3024-4102-b22e-baef2ac4b1fe.png align="center")
    
2. `clear`: This command clears the terminal screen, giving you a fresh, clean slate. It's like tidying up your workspace by removing all the clutter and starting anew. Just type `clear`, and all previous output will be cleared from the screen.
    
3. `exit`: When you're done working in the terminal, this command lets you gracefully exit or close the terminal session. It's like saying, "I'm finished here, goodbye!" Simply typing `exit` will close the terminal window or end the session.
    
4. `logout`: Similar to the `exit` command, `logout` is used to log out of a user session. It's like signing out of your account before leaving a computer. Typing `logout` will end your current session and return you to the login screen.
    
5. `history`: This command shows you a list of the commands you've previously executed in the terminal. It's like viewing a timeline of your past actions. Running `history` will display a numbered list of your command history, making it easier to recall or reuse commands you've used before.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1685698814265/a1ce6a7f-9a25-4acc-b170-48acde09b635.png align="center")
    
6. `history -d <number>`: With this command, you can delete a specific command from your command history. For example, if you want to remove command number 7 from your history, you would run `history -d 7`. It's like selectively erasing a single entry from your command log.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1685698863250/c39841e3-6c21-4278-b2b2-d61e2110a9be.png align="center")
    
7. `history -c`: This command clears your entire command history. It's like wiping the slate clean and starting fresh. Typing `history -c` will delete all the entries in your command history, providing a blank history for future commands.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1685698893292/9482f74d-8eac-4346-a47d-7eb864e38287.png align="center")
    

## System Commands

1. `uname -r`: This command displays the kernel release version of the operating system. For example, running `uname -r` might show "4.18.0-305.el8.x86\_64" on Red Hat.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1685698930227/039e82a1-74b4-451e-98f7-dab422415608.png align="center")
    
2. `cat`: The `cat` command is short for "concatenate" and is used to display the contents of a file. For instance, running `cat file.txt` would display the contents of "file.txt" in the terminal.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1685699016606/ed50669e-9132-495a-a55d-d2d83a196949.png align="center")
    
3. `uname -s`: This command shows the operating system name. For example, running `uname -s` might display "Linux" on a Red Hat system.
    
4. `uname -n`: Running `uname -n` displays the system's network node hostname. It provides the name of the machine in a network.
    
5. `uname -p`: This command displays the processor type or architecture of the machine. For example, it might show "x86\_64" on a 64-bit Intel or AMD processor.
    
6. `uname -m`: Running `uname -m` provides information about the machine's hardware architecture. It might display "x86\_64" for a 64-bit system.
    
7. `uname -o`: This command shows the operating system's vendor or origin. For example, it might display "GNU/Linux" on a Red Hat system.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1685699124315/72c036b8-0701-43e0-9113-54c4bb313e9a.png align="center")
    
8. `cat /proc/cpuinfo`: Running this command displays detailed information about the CPU(s) in the system, such as the model, speed, and cache size.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1685699160421/38180018-6740-4f0f-bf17-1445a0911126.png align="center")
    
9. `lscpu`: The `lscpu` command provides comprehensive information about the CPU(s) in a more structured format. It displays details like architecture, cores, threads, and cache sizes.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1685699313185/8200eba7-93d6-4623-a26d-6fce639a7694.png align="center")
    
10. `lsusb`: Running `lsusb` lists the USB devices connected to the system, providing information about the manufacturer, model, and version of each device. \[This you can try on your VM Machines\]
    
11. `cat /proc/meminfo`: This command displays information about the system's memory usage, including total memory, available memory, and usage statistics.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1685699395576/4b8cc33a-2cff-4502-9a6f-20f7fe58c443.png align="center")
    
12. `free`: The `free` command provides an overview of the system's memory usage and availability, displaying values such as total, used, and free memory.
    
13. `free -m`: Running `free -m` displays the memory usage in megabytes, providing a more human-readable format.
    
14. `free -g`: This command shows the memory usage in gigabytes when you run `free -g`.
    
15. `free -h`: Running `free -h` displays the memory usage in a human-readable format with units like GB, MB, and KB.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1685699455538/0dd504db-8264-49e9-83c5-aaa54b563c7d.png align="center")
    
16. `lspci`: The `lspci` command lists the PCI (Peripheral Component Interconnect) devices connected to the system, showing details about the hardware components.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1685699489355/22577e33-d096-43bf-be90-66aa13500b41.png align="center")
    
17. `dmidecode`: Running `dmidecode` displays detailed information about the system's hardware, including BIOS, motherboard, memory, and more.
    
18. `hostname`: This command displays the current hostname of the system.
    
19. `hostnamectl`: Running `hostnamectl` provides detailed information about the system's hostname configuration and settings.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1685699538593/91067bf1-18ed-44b3-992f-3bd4f3215c2a.png align="center")
    
20. `ifconfig`: The `ifconfig` command shows the network interface configuration, including IP addresses, MAC addresses, and other network-related information. Note that this command is being replaced by `ip` command in newer systems.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1685699560462/151b66e3-98df-49f9-b5c2-9af192a9beb8.png align="center")
    
21. `ip addr` or `ip a s`: Running `ip addr` or `ip a s` displays detailed information about the network interfaces and their configurations.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1685699596790/abc8dd1a-cc18-475b-b1de-e8fe4788ff9f.png align="center")
    
22. `ip a`: This command shows the IP addresses assigned to the network interfaces.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1685699626809/14c8e358-2ab1-4922-8cb8-51b78ea1bf94.png align="center")
    
23. `nmcli`: The `nmcli` command is used for network management, allowing you to control and configure network connections, devices, and settings.
    
24. `ping`: Running `ping` followed by an IP address or domain name sends ICMP echo requests to check network connectivity and measure response times.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1685699667526/2eb6fbc4-ba5a-438e-acd9-c0d66b15a0ae.png align="center")
    
25. `du`: The `du` command shows disk usage, displaying the size of files and directories.
    
26. `du -s`: Running `du -s` provides a summary of the disk usage, displaying the total size of a directory.
    
27. `du -h`: This command displays disk usage in a human-readable format, using units like GB, MB, and KB.
    
28. `du -sh`: Running `du -sh` shows the summarized disk usage in a human-readable format.
    
29. `lsblk`: The `lsblk` command lists block devices, such as hard drives and partitions, providing information like sizes and mount points.
    
30. `df -h`: Running `df -h` displays disk usage information for file systems in a human-readable format, showing sizes, used space, and available space.
    
31. `df -hT`: This command provides a detailed overview of disk usage, including file system types, sizes, used space, available space, and mount points.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1685699757405/cca0c419-bb98-49ad-b7ef-7392d45812b2.png align="center")
    
32. `reboot`: The `reboot` command is used to restart the system. It initiates a graceful system restart.
    
33. `init 6`: Running `init 6` also restarts the system, similar to the `reboot` command.
    
34. `shutdown`: This command initiates a system shutdown, allowing you to safely turn off the computer.
    
35. `init 0`: Running `init 0` is another way to shut down the system, similar to the `shutdown` command.
    
36. `shutdown -r`: This command shuts down the system and immediately restarts it.
    

## Help Commands

1. `man`: The `man` command is used to access the manual pages for various commands and topics. It provides detailed documentation and instructions on how to use specific commands. For example, running `man ls` will display the manual page for the "ls" command, showing information about its usage, options, and examples.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1685699785567/2f5a9acf-0999-41bc-bc1f-b6bb37247dae.png align="center")
    
2. `help`: The `help` command is a built-in command in many shell environments, such as Bash. It provides a concise overview of the available built-in commands and their usage. Running `help` without any arguments will display a list of built-in commands, and running `help <command>` will show information about the specific command.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1685699822611/de9f65e8-3521-41d9-97bf-61af0884a0c8.png align="center")
    
3. `which`: The `which` command is used to find the location of an executable file in your system's PATH. For instance, running `which ls` will display the path to the "ls" command, indicating its location in the system.
    
4. `whereis`: The `whereis` command is used to locate the binary, source, and manual page files for a specific command or program. Running `whereis ls` will display the paths to the binary, source, and manual page files associated with the "ls" command.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1685699878768/f8788cc1-d19b-447d-b065-8a55dd5a433f.png align="center")
    
5. `info`: The `info` command is used to access the documentation in the GNU Info format. It provides comprehensive and structured information about various topics, including commands, utilities, and system configurations. Running `info <topic>` will display the relevant information in the Info format. For example, `info ls` will provide detailed documentation on the "ls" command and its options.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1685699905932/d53d857f-b749-4d43-ae50-f9cb13e1e398.png align="center")
    

## File Creation

1. `touch`: The `touch` command is used to create new files or update the timestamp of existing files. If the file specified doesn't exist, it will be created. For example, running `touch file.txt` will create a new file called "file.txt" in the current directory or update its timestamp if it already exists.
    
2. `touch -d <date>`: With the `-d` option, you can specify a specific date and time to assign to a file's timestamp. For instance, running `touch -d "2022-01-01 12:00:00" file.txt` will set the timestamp of "file.txt" to January 1, 2022, at 12:00 PM.
    
3. `touch -a`: The `-a` option updates only the access timestamp of a file, leaving the modification timestamp unchanged. It's useful when you want to indicate that a file was accessed or read without modifying its content. For example, running `touch -a file.txt` will update the access timestamp of "file.txt".
    
4. `touch -m`: The `-m` option updates only the modification timestamp of a file, leaving the access timestamp unchanged. It's useful when you want to indicate that a file was modified without changing its access status. For example, running `touch -m file.txt` will update the modification timestamp of "file.txt".
    
5. `touch -r <reference_file>`: With the `-r` option, you can set the timestamp of a file to match that of a reference file. For example, running `touch -r reference.txt file.txt` will set the timestamps of "file.txt" to match those of "reference.txt".
    
6. `ls`: The `ls` command is used to list the files and directories in a directory. Running `ls` without any arguments will display the contents of the current directory. For example, running `ls` will show a list of files and directories in the current directory, including their names and some additional information like permissions and timestamps.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1685700184808/deb3b858-27cf-4220-8280-61ee9740c632.png align="center")
    

The `touch` command is primarily used for managing file timestamps, while `ls` is useful for viewing the contents of directories.