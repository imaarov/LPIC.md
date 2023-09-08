## Basic Commands

- ### tty comamnd showing which tty this terminal use
```bash
> tty
> /dev/pts/0
```
- ### whoami show current user name
```bash
> whoami
> sarv
```

- ### pwd comamnd showing which directory we are in right now
```bash
> pwd
> /home/sarv
```

- ### ls comamnd showing list of files & directories
```bash
> ls -h (Human readable) -a (show dot files, hidden files) -l (show permissions)
> (Permission) (User name)   (Size)(Created at&Updated at) (Name)
> drwxr-xr-x. 1 sarv sarv     324 Aug 13 13:22  Desktop
> drwxr-xr-x. 1 sarv sarv     934 Jul 13 22:08  Documents

```

- ### cd comamnd change directory to target one
```bash
> cd /var/log
> cd ../../
> cd -  (go to last directory)
> cd ~  (go to home)
```

## Linux Detail Commands

- ### uname command show kernel info
```bash
> uname
> Linux
> uname -r
> 6.4.7-100.fc37.x86_64
> uname -v	#Time of kernel compiled
> #1 SMP PREEMPT_DYNAMIC Thu Jul 27 19:56:37 UTC 2023
> uname -a	#All info
> Linux fedora 6.4.7-100.fc37.x86_64 #1 SMP PREEMPT_DYNAMIC Thu Jul 27 19:56:37 UTC 2023 x86_64 x86_64 x86_64 GNU/Linux

```

## Commands of Command
- ### type command show if command is a built-in or external command
```bash
> type pwd
> pwd is a shell builtin
```

- ### man command show manual of command
```bash
> man uname
```

## Display content Commands
- ### ls command
```bash
> ls -a
> ls -F
```
- ### cat command display file content
```bash
> cat /etc/hostname
> localhost
```
- ### head command display first 10 line from file content
```bash
> head /var/log
> head -n (number of line) /var/log
```
- ### tail command display last 10 line from file content
```bash
> tail /var/log
> tail -n (number of line) /var/log
> tail -f /var/log	#show live log in terminal
```

- ## Pager
- ### more comamnd show long info or long log in pager
```bash
> more /var/log/boot.log

```
- ### less comamnd show long info or long log in pager
```bash
> less /var/log/boot.log

```

- ### wc command show how many word and lines and bytes in a file
```bash
> wc /var/log/boot.log
```
- ### uniq command show how many time a line occurs
```bash
> uniq -c /var/log/boot.log
```
- ###  echo command to print a text
```bash
> echo "some" > some.txt		#put some in some.txt file
```

## Manipulating Text File

- ### touch command create a new file
```bash
> touch sample.log
```
- ###  echo command to print a text
```bash
> echo "some" > some.txt		#put some in some.txt file
```
- ###  sort  command sort file content base on alphabet
```bash
> sort sample.log
```
- ###  paste command combine two file content together 
```bash
> paste sample.txt sample.log #(and multiple other file can be used)
> text 1
> some 2
> word 5
```
- ###  split command split file content to other files
```bash
> split -l 2 sample.log #(File Base Name)
```
- ###  tr command replace word or character in a file with other word
```bash
> tr : $ < /var/log/some.log	#Replace : to $ in output of content of some.log file
```
- ###  od command display file content(Binary code files) base on octal or hexa format
```bash
> od /bin/pwd
> od -A x -t x1z -v /bin/pwd
```

- ###  sed command replace word in every first line of file content and  display it
```bash
> sed 's/changeThis/chageToThis/' some.txt
```

## Search text file

- ###  grep command used for searching in a file or content
```bash
> grep root /var/log
> grep --color=never root /var/log	#show without color
> grep -i	#caseinsensitive
> grep ^root /var/log	#search where start with root
> grep root$ /var/log   #search where end with root
```

## Redirecting IO

- ### < redirect (INPUT) the right side content to left side command
```bash
> tr : $ < /var/log/some.log	#Replace : to $ in output of content of some.log file
```

- ### > redirect (OUTPUT) the left side content store in right side file
```bash
> echo "hi" > sample.txt
> grep  bash$ /etc/passwd > sample.txt
```

- ## Pipes (pass the output of first command to input of the second one) |
```bash
> gerp nologin$ /etc/passwd | wc -l
```

## Searching

- ### remove Error from display with ( some command 2> /dev/null ) 

### Regex
- ### in regex [46] its 4 or 6 and [4-6] its a range from 4 to 6 
- ### regex with grep
```bash
> grep  -d skip -i --color=none ipv[46] /etc/*	#search for ipv4 or ipv6 in all etc sub directories
> grep -d skip -i --color=none ipv[46] /etc/* 2> /dev/null	# remove error from displaying
> grep --color=none ro*t /etc/passwd		#start with r hase zero or more o in it and end with t
> grep -E ro+t /etc/passwd #start with r hase one or more o in it and end with t must use -E with command (Extended regex)
> grep -E ro?t /etc/passwd	#start with r and hase zero or one o in it and end with t
> grep -E root\|shutdown /etc/passwd		#search for root or shutdown
> grep -E "root|shutdown" /etc/passwd
> grep -E "(^root|^shutdown).*bash$" /etc/passwd	#start with root or shutdown end with bash
> sed 'a/cake$/cookies/' foos.txt	#replace cake in the end with cookies in output
```
## Finding files and info of that

```bash
> which sed	#command location file
> ls -F /bin/sed
> /bin/sed*	#* its mean that its executable
> type grep
> grep is aliased to ...
> unalias grep	#remove grep alias
> whereis grep	#show bin directory and man page
```

## Test Searching 
```bash
> man -k which | grep ^which | tee studyMe.txt
> man -k whereis | grep ^whereis | tee -a studyMe.txt
```

- ### locate command find the file
```bash
> locate word.txt
> /home/sarv/Downloads/word.txt
```
- ### find command
```bash
> find /home -regex .*word.txt
> find /etc -maxdepth 1 -name passwd	#search one directory depth
```

## Wild card

- ### some* -> mean anything after some is accept and \*some* mean before and after some anything is accepted
- net? -> accept anything in one character like nets or netv  

## Create and Edit file
- ### touch command create a file if its not exists and update timestamp if file exists
```bash
> touch some.txt
> rm some.txt	#delete some.txt file
> rm -i some.txt	#asking before delete
> rm -vi some.txt #ask and show deleted file info
```
## Copy and Move files

```bash
> cp some.txt /home/somewhere/
> cp some.txt /home/somewhere/somecopy.txt
> mv some.txt /home/somewhere
> mv some.txt /home/somewhere/somemoves.txt
```
## Create and Edit directory
```bash
> mkdir somedirectory
> mkdir -p newdir/anothernewdir	#create a parent dir with the child one
> rmdir somedir	#only delete EMPTY DIR
> rm -irf somedir	# delete whole dir with its child file and directories
> cp -r somedir /home/somewhere/newdir	#copy dir
> mv somedir /home/somewhere/newdir	#moving dir
```

## Compressing files

- ###  gzip or bzip2 or xz will remove files after compressing
```bash
> # Zip files:
> gzip file1	#file1.gz
> bzip2 file2   #file2.bz2
> xz file3		#file3.xz
> # Unzip:
> gunzip file1.gz
> bunzip2 file2.bz2
> unxz file3.xz
> # See content of zip file:
> zcat file1.gz
> bzcat file2.bz2
> xzcat file3.xz
> # Tar Archive
> tar -cvf exportName.tar file? # Archive the files 
> tar -tf archive.tar # see content of tar 
> tar -xvf archive.tar	# file will not remove
> ls file? | cpio -ov > archive.cpio	#archive with cpio with all files that passed
> dd if=/dev/sda of=/dev/null status=progress	#copy whole disk
```

## Text editors (Emacs, nano, vi)

- ###  nano
```bash
> # Zip files:
> nano some.file	#Create or edit 
> vi some.file		#open in vim editor
> # Command mod or normal mod
> # by enter i command now are in insert mod for writing codein the file
> # Escape key for backing in Command mod
> # :w	#for written in file
> # :wq #quit the editor
> # :x #save content and quit the editor
> # Shift + z + z for save and quit the editor
```
- ### Navigation in vi
```bash
> # j key for jump down line k key for going upper line
> # jump in first of the line Shift + ^
> # jump in end of the line Shift + $
> # / for searching
```

- ### Some commands
```bash
> # o Enter in a new line after the current line 
> # d for deleting line
> # dw for deleting the word
> # Shidt d for deletign line
> # u for undo 
> # d3d delete 3 lines of code
> # :set number # set number in each lines
```

## File Permissions

- ###  file permission
```bash
> ls -l some.file
> -rw-r--r--. 1 imaarov imaarov 128553 Sep  1 16:58 some.file
> #<file/directory permission> <owner> <group> <size> <date of modified> <name>
> # file object types (file type codes) first letter in start of permission section in above code
> # File (-)
> # Directory (d)
> # Symbol link (l)
> # Block device (b)
> # Character device (c)
> ls -l /dev/sda
> # File Permission are next 9 characters after file type code 3 sets of 3
> # Owner permissions Group permission World permission (Other)
> # rwx- => read write execute no permission
> whoami	# See Your username (Owner Name)
> groups	# See all the group
> id -Gn	# It shows a list of group names associated with the user's account
> id -gn	# primary group name of the user 
```
- ### Change Permissions
```bash
> ls -l some.file
> -rw-r--r--. 1 imaarov imaarov 128553 Sep  1 16:58 some.file
> chgrp NewGroup some.file	# Change file group to NewGroup
> sudo chown root some.file	# Chage file ownership to root
> sudo chown root:NewGroup 	# Change file owner&group to root&NewGroup
> chown :NewGroup	# Change the group
> # Symbolic mode levels: u for owner, g for group, o for other(World), a for All (owner + group + other)
> # + for add permission(s)
> # - for remove permission(s)
> # = for set listed permission(s)
> #	rwx => read write execute
> chmod a=rw some.file	# set read & write permission for all
> chmod o-r some.file 	# subtract read from other permission
> chmod u+w some.file	# add write permission for user(owner)
> chmod u+r,g-x some.file	#add read to owner and  subtract execute group
> # Octal mode
> # 0 is no permission
> # 5 is read and execute permission
> # 6 is read&write permission
> # 7 is read&write&execute permissions
> # #3 digits => first is for owner second for group and last digit is for world or other permission
> # Special permission
> # SUID: SUID (Set User ID): When the SUID permission is set on an executable file, it allows the file to be executed with the privileges of the file owner instead of the user executing it. This is useful for granting temporary elevated privileges to specific users to perform certain tasks. For example, the `passwd` command has the SUID permission to allow regular users to change their own passwords.
> # GUID: GUID (Set Group ID): Similar to SUID, the GUID permission is used on executable files. When the GUID permission is set on a file, it allows the file to be executed with the privileges of the group owner instead of the user executing it. This can be useful in scenarios where multiple users belong to the same group and need to execute a file with group-level permissions.
> # Sticky bit:Sticky Bit: The sticky bit permission is primarily used on directories. When the sticky bit is set on a directory, it restricts the deletion or renaming of files within that directory to only the file owner, the directory owner, or the root user. This is commonly used on directories such as `/tmp` to ensure that users can only delete or modify their own files and not interfere with others.
> # SUID => chmod u+s some.file
> # SGID => chmod g+s some.file
> # Sticky bit => chmod o+t some-directory
> 
```
- ### Default Permissions
```bash
> # default file permisssions on creat are 0666 or rw-rw-rw
> # default directory permission on creat are 0777 rwxrwxrwx
> umask
> 022
> # 0-nopermission 1-executePermission 2-writePermission 3-executeWrite 4-readPermission 5-executeRead 6-readWrite 7-allPermission
> # first digit refer to owner, second group, and last for world (for 3 digits if it was 4 digits first one is special permission)
> umask 0027	# Change creation mask THAT CHANGE THE DEFAULT PERMISSION IN THIS USER  
``` 

- ### Hard & Soft links
```bash
> # Soft links are is just another pointer to a file name
> # Soft link => Original file name => inode # => File data on storage device
> ln -s pointToMe.file linkerFile	# Create a soft link of pointToMe.file that have name of linkerFile
> # Hard link are like that giving a file two name
> # Hard link => inode # => File data on storage device
> ln some.file someHardLink	# Create a hard link
> ls -i # show the inode number (if two files have same inode number then they are hard link)
```

## Processes

- ###  display process(running program)
```bash
> ps
>     PID(id) TTY(which terminal its running)          TIME(cpu usage) CMD(name)
>   36805 pts/0    00:00:01 zsh
>   57186 pts/0    00:00:00 ps
> pgrep bash
> 35633
> pgrep -u imaarov #display the process of your user
> pgrep -au imaarov # show all info with a option
> pgrep  -at tty2	# shwo all the process of the tty2 terminal
> ps -elf	#show all process with more info PPID(Parent Process Id)
> # number in start in above command 4 => sudo
> ps -elf | grep ^F
> F S UID          PID    PPID  C PRI  NI ADDR SZ WCHAN  STIME TTY          TIME CMD

> # R -> Running, S -> Sleeping , D -> Uninterruptible sleep, T -> Stop, Z -> Zombie, I ->  The process is currently idle or sleeping.
```
- ### Monitoring  Processes
```bash
> top	# Show usage of cpu memory and process in order of their usage
> uptime
>  19:52:55 (how long system up) up  5:01,  1 user (number of logged users),  load average: 1.06, 1.04, 0.82 (cpu load avarage it should not be one or above )
>  free  # see how much ram is free (for human readable set -h)
>  free -h 
```
- ### Jobs (process)
```bash
> sleep 30 # you can stop by Ctrl + z, to restart 
> bg 1  # restart the job in background
> jobs 	# see the jobs
> sleep 6000& # & send the job to background
> fg 2	# set the job in forground
```
- ### Signals
```bash
> sleep 4000& # send this job in bg
> jobs -l # see all jobs
> # Signals are defined by number, word or start with SIG
> # SIGHUP(1) # Signal send to process to terminate the process when user logs out
> # SIGKILL(9) # Unconditionally kill a process
> # SIGTERM(15)  # Terminate the signal if its possible
> kill -s SIGKILL 2010(id of process)	# Send SIGKILL to kill the job of that process id
> pkill -15 -g 2250
> killall sleep	#send KILlALL signal to all sleep
> nohup sleep 4444&	# ignore the SIGHUP signal for this process
```
- ### Process Priority(for jobs and process that need access cpu, lower pri access first)
```bash
> sleep 7000&
> ps -l 4345
> F S   UID     PID    PPID  C PRI(priority)  NI ADDR SZ WCHAN  TTY        TIME CMD
0 S  1000   64540   61199  0  80   0 - 55331 hrtime pts/2      0:00 sleep 400
> nice -n 19 sleep 3000&	# set the prioty to 99 an NI to 19
> sudo nice -n -20 sleep 300&	#set the negative NI to get faster access to cpu
> renice  +5 23232	# set nice level to 5
> # Renice useing top
> top -> Shift + l

```

## Environment Variables

- ###  env vars
```bash
> echo $USER
> imaarov
> echo $LOGNAME
> imaarov
> echo $EDITOR # not set by default
> echo $VISUAL # not set by default
> echo $PWD	# current directory
> echo $PS1	# see the prompt
> env | less 	# see the list of all env variables
> printenv HOME # Show env var
> echo $HISTFILE
> ls $HISTFILE	# show history commands file
> echo $HISTSIZE	#max command storage
> echo $UID	# see user id
> echo $GROUPS
> echo ${GROUPS[*]}	# show group id of all groups
> echo $BASH_VERSION
> echo $HOSTNAME # cat /etc/hostname
> echo $LANG
> # LANG -> overall locale vars
> # LC_ALL 	->  overall locale vars that required on some distro
> # LC_* -> Refer to other locale vars
```
- ### Path env
```bash
> echo $PATH	#all directories that contain command that we use in terminal
> PATH=$PATH:/home/someNewDir	# add someNewDir to PATH
> echo $PS1
> PS1="~ "	# set the env var PS1 to ~
```
- ### Subshell
```bash
> echo $SHLVL	# subshell is number of bash shell you start in a shell
```

## Mass Storage Device Terms

- ###  disks, partitions, file systems
```bash
> ls /dev/sda	# A Full disk
> ls /dev/sda?  # List of partitions
> lsblk	#show disks partitions
> # TYPEs: disk -> full disk, part -> partition, lvm -> logical volume (group on or more partition to grew together)
> cat /proc/partitions
> cat /proc/filesystems	#nodev is not support
> lsblk -f # see file system
```
- ### SATA, SCSI, USB
```bash
> ls /dev/sd* # Disks
> ls /dev/sr* # Optical drive
> ls /dev/fd? # FLoppy drive
```
- ### Logical Volumes & Btrfs
```bash
> lsblk -f /dev/sda2
> lsblk -p /dev/sda2
> ls -l /dev/mapper
```
- ### btrfs use B-tree data structure to read and write data
- ### Mass Storage Device info
```bash
> lsdev	#low level device info use dma+interrupts+ioports
> ls /proc/dma
> cat /proc/interrupts
> cat /proc/ioports
> ls /dev/disk/by-id
> ls /dev/disk/by-id	# all the attached storage devices by their IDs
> ls /dev/disk/by-uuid	# all the attached storage devices by their UUID 
```

## Low Level Hardware Info

- ###  disks, partitions, file systems
```bash
> ls -l /dev/sda /dev/tty2
> cat /proc/devices	
> pvs # for showing physical volumes in LVM
> gvs # for showing volumes groups in LVM
> cat /sys/block/sda/sda1/size # size of partiotion sda1 in sda disk
> lsblk -o NAME,LOG-SEC /dev/sda1 # display the block device name and logical sector size for the partition "/dev/sda1"
> lsblk -s
```
- ### PCI
```bash
> lspci	#show all the device connected to this system and pci busses info
> # PCI : Peripheral Component Interconnect
> # It is a computer bus standard that is used for connecting peripheral devices to the motherboard of a computer
> lspci -vv	#showing with info
> lspci -tv # show with detail and tree mode
> ls -l  /dev/disk/by-path	#showing disk partiotions by their path (pci busses)
> readlink -f /dev/disk/by-path/pci-0000:00:1f.2-ata-1.0-part1 # to see where this soft link point to
> /dev/sda1
```
- ### Drivers 
```bash
> ls /lib/modules/6.4.7-100.fc37.x86_64/kernel/drivers #show drivers
> lsmod # show drivers&modules .ko
> sudo rmmod joydev # remove the joydev kernel module
> sudo insmod /lib/.../jodev.ko	#insert the module
> sudo modprobe -v dm_mirror # load the module
> sudo modprobe -rv dm_mirror # remove the module and all its depencies  
```
- ### Hot plug/Cold plug
```bash
> # Cold plug are device that have pluged before the system boot
> # udev is a service or Daemon that setting up the file in dev directory for a cold plug and network interface cards and hot plug device(like /dev/sda1 for cold plug or USB for hot plug)
> ls -d /media	# hot plug
> ls /etc/udev/rules.d/ # udev rules
> # DBUS is service or Deamon provide message communication service for other services
```

## Manage Storage

- ###  manage partitions
```bash
> cat /proc/partiotions	# show partiotion
> # Disk Partition Table - Partition Type its data structure let os know partitions located on disk and sizes
> # MBR (master boot record) - Table stored in first sector on disk Size of 2.2 TB Partision type: primary - logical -extended
> # GPT - GUID Partition Table unlimited number of partitions - no partition type table header stored in 2nd disk sector entries stored in the 3th to 34th disk sector
> sudo  gdisk /dev/sdb # Makee Partition the disk to GPT
> # n for new partition in gdisk
> # then partition number
> # first sector: default by enter
> # partition size like: +1G 
> # type : default by enter
> # after that you can see your partition by i command
> # finally w for writting the partition on disk
> sudo fdisk /dev/sdc # for mbr or gpt
> # start making partition by pressing n
> # p for primary
> # partition number : default 1
> # first sector default
> # size: like +1G
> # finally w for writting 
> sudo parted /dev/sdc # making partition
> # print # to see what is on this drive before make partition
> # mkpart primary (start after the last partition end like 3233) (ending location)
> # quit for quit the parted
> lsblk -f | grep -E "sd[abc]?"	# see disks and partitions and filesystems of that
> grep ext4 /proc/filesystems 	# see filesystem is supported
> ls /lib/modules/6.4.7-100.fc37.x86_64/kernel/fs # loaded filesystem module in linux kernel
> sudo mkfs -t ext4 /dev/sdb1	# format and make ext4 filesystem
```
- ### Mounting
```bash
> sudo mount -t ext4 /dev/sdb1 /tmp	# mount sdb1 on tmp
> mount # see all mount
> umount temp # unmount
> cat /etc/fstab
> # -****************************************************-#
> df -h # disk free space
> du -sh /home/imaarov/Documents # size of Docuemtns
> du -s --inodes /home # number of inodes
> df -i	# ow many inodes are used and free 
```
- ### Tuning File System
```bash
> lsblk -f | grep -E "sd[abc]?"
``` 
- ### Repair File Systems
```bash
> fsck	# check and optionaly repair filesystem the unmounted partitions
> fsck -r /dev/sda2
> e2fsck /dev/sda2
```

## Run Levels

- ###  run level
```bash
> runlevel
> # 1 -> all services stopped
> # 2 -> single user mode # Only root can loggin to system
> # 3 -> multi-user mode # network service provided # no gui
> # 4 -> user customizable
> # 5 -> multi-user mode # network services & gui
> # 6 -> reboot
> ls -d /etc/rc.d/rc?.d	# run levels config & script
> grep ^id /etc/inittab # default run level
> init 3 # go to run level 3
> systemctl list-unit-files # services and deamons
> # enabled: start service as system boot
> # disable: wont start service at system boot
> # static: only starts service if  manually started or another service needed at boot
> systemctl cat syslog.service
> ls /etc/systemd/system # service
> # Manage services
> systemctl status network-manager	# status of this service
> sudo systemctl stop network-manager # stop the service
> sudo systemctl start network-manager # start the service
> sudo systemctl disable network-manager # its not start a system boot
> sudo systemctl enable network-manager
> wall # sending message
> shutdown +5 "shutdown in 5 sec"
```

## Package Managers

- ###  Manage Debian Package Manager
```bash
> # .deb or .rpm
> # apt, yum, zypper
> # debian based: apt 
> # red hat based: yum, zypper
> ls gimp*.deb
> gimp_2_amd64.deb
> dpkg -c gimp_2_amd64.deb # view package content
> dpkg -I gimp_2_amd64.deb # version and dependencies
> dpkg -s gimp # is Installed only name ?
> sudo dpkg -i gimp_2_amd64.deb #install package
> sudo dpkg -V gimp
> sudo dpkg -C gimp	# you can give a package name
> sudo dpkg -r gimp # remove package
> which dpkg-reconfigure
> sudo dpkg-reconfigure apparmor
> 
> cat /etc/apt/sources.list # see package repositories
> sudo apt-get update # update repositories
> sudo apt-get install procinfo # install & update
> sudo apt-get remove procinfo # uninstall package
> apt-cache depends procinfo # any package dependencied (like procinfo)
> apt-cache showpkg procinfo # show more info
```
- ### Manage RedHat Package Manager
```bash
> ls *.rpm 	# .rpm is for red hat package extention
> rpm -q firefox # check if the package or app is installed or not
> rpm -iv iotop-0.6-4.e17.noarch.rpm # install the package
> rpm -u iotop-0.6-4.e17.noarch.rpm # udpate or install the package
> rpm -e iotop # uninstall the package
> rpm -V iotop # check integrity of the package
> rpm -qi iotop # packge info
> rpm -qR iotop # package Dependencies
> rpm --whatprovides /bin/top # package name of binary file
> 
> less /etc/yum.conf
> ls /etc/yum.repos.d/ # diffrent repositories
> yum list iptraf-ng # its installed or not
> yum install iptraf-ng
> yum clean all # clean cache
> yum update iotop # update the package
> yum remove iotop # remove the package
> yum info iotop # info of package
> yum deplist iotop # show dependencies
> yum provide /bin/top # show the name of binary package
> yum search lib # see all the package with this pattern in it
> # Zypper 
```

## Libraries

- ###  library
```bash
> ls /lib/
> ldd /usr/bin/man # display all library that man binary needed
```

## Virtualization

- ###  on linux
```bash
> # first is your bios support virtualization? go check it in bios ~ /proc/cpuinfo
> # enough free memory ? ~ free
> # free disk ? ~ df
> # network interface cards ? NICs
> grep ^flags /proc/cpuinfo | grep vmx # cpu support vm intel ?
> grep ^flags /proc/cpuinfo | grep svm # amd
```


## Other Command
- ### history command show commands history
```bash
> history
>  3987  uname -r
>  3988  uname -v
>  3989  uname -a
> !3989   #run 3989th command from history (uname -a)
> !! #last command
> lsblk #show disks
> dmesg # show boot log
> pstree
```

- ### man comamnd show manual of command
```bash
> man uname
```