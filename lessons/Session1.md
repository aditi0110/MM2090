# Getting to know your machine and account

Packages needed for this session: 
  * [hwinfo](https://packages.ubuntu.com/focal/hwinfo)
  * [lshw](https://packages.ubuntu.com/focal/lshw)
  * [fdisk](https://packages.ubuntu.com/focal/fdisk)
  * [memtester](https://packages.ubuntu.com/focal/memtester)
  * [hardinfo](https://packages.ubuntu.com/focal/hardinfo)
  * [util-linux](https://packages.ubuntu.com/focal/util-linux)
  * [clinfo](https://packages.ubuntu.com/focal/clinfo)
  * [net-tools](https://packages.ubuntu.com/focal/net-tools)
  * [coreutils](https://packages.ubuntu.com/focal/coreutils)
  * [procps](https://packages.ubuntu.com/focal/procps)
  * [pciutils](https://packages.ubuntu.com/focal/pciutils)
  * [dmidecode](https://packages.ubuntu.com/focal/dmidecode)
  * [lsb-release](https://packages.ubuntu.com/focal/lsb-release)
  * [hdparm](https://packages.ubuntu.com/focal/hdparm)

Use "sudo apt-get install \<package\>" to install the above packages.

To search for which package a particular executable, say, hwinfo came from:

    /usr/bin/sudo apt-get install apt-file
    /usr/bin/sudo apt-file update
    /usr/bin/apt-file search hwinfo

This works only if you have already installed the package. If you want to find which package to install to have a particular executable, you need to search the internet with appropriate keywords.

## Hardware of the machine

This section is to let you know about the following peices of hardware you have in your machine: CPU, Memory, Hard Disks, Graphics Card, Monitor Network Cards

### hwinfo
The program **hwinfo** comes from the package **hwinfo**. This command gives a long and comprehensive listing of hardware.

    /usr/sbin/hwinfo 

You can redirect the output to a file in your home directory and read it. Use arrow keys to scroll up and down. Press q to quit reading the file. You can do this to look at the output of other commands too.

    cd
    hwinfo > hwinfo.txt
    less hwinfo.txt

### lshw
The program **lshw** comes from the package **lshw**. This tool provides a brief listing of hardware.

     /usr/bin/lshw


### /proc/cpuinfo
You can read the contents of this virtual file and explore what cpu you have, how many cores, speed, cache memory etc.

     /bin/cat /proc/cpuinfo 

### /proc/partitions
List the partitions mounted. Use the command **mount **or** df** to see similar information.

      /bin/cat /proc/partitions

### df
The program **df** comes from the package **coreutils**. Explore other options of df to display the details on filesystems mounted.

      /bin/df -h 

### fdisk
The program **fdisk** comes from the package **fdisk**. Use with care as you will be running it as a super user. One may accidentally cause an edit to the partitions, format etc., so be careful with this command. 

      /usr/bin/sudo /sbin/fdisk -l 

### lsblk
Figure out the device and the partitions being used for storage in your machine.

     /bin/lsblk -o NAME,SIZE

### lspci
The program **lspci** comes from the package **pciutils**. Explore what hardware components are associated with the PCI bus. 

     /usr/bin/lspci 

### top
The program **top** comes from the package **procps**. Press q to quit the display. Watch the listing of processes while you open other applications and close them. Explore the meaning of numbers shown in the header of the screen.

    /usr/bin/top 

### lshw
The program **lshw** comes from the package **lshw**. Explore other sections under which lshw gives the output.

     /usr/bin/lshw -c display

### dmesg
The program **dmesg** comes from the package **util-linux**. It outputs the system log from the booting onward.

    /bin/dmesg

### free
The program **free** comes from the package **procps**. Use with option -h for human readable format of free and used memory. 

      /usr/bin/free -h


### dmidecode
The program **dmidecode** comes from the package **dmidecode**. Explore what type of memory you have, of what speed etc., Explore what other types of hardware this command can give you details about. Redirect the output to a file and read it.                 

     /usr/bin/sudo /usr/sbin/dmidecode --type memory                    

### memtester
The program **memtester** comes from the package **memtester**. Check for any errors in your memory. In the command given, 24MB of data and 2 iterations are being used to make this test.                        

     /usr/sbin/memtester 24M 2         

### hardinfo
The program **hardinfo** comes from the package **hardinfo**. This tool has a graphical user interface and can export a report of your hardware.          

 /usr/bin/hardinfo                  

### upower
The tool **upower** comes from the package **upower**. Run with -e option to see which option to be used for \<battery\> (the one containing the string BAT). Run "upower -i \<battery\>" to see the status of your battery.                          
     /usr/bin/upower -e
     /usr/bin/upower -i <battery>

### lscpu
The tool **lscpu** comes from the package **lscpu**. List CPU information of the machine.

      /usr/bin/lscpu 

### clinfo
The tool **clinfo** comes from the package **clinfo**. See the capabilities of CPU and GPU to run OpenCL codes. The output will not be much if you do not have a good enough GPU in your machine.

      /usr/bin/sudo /usr/bin/clinfo 

### hdparm
The tool **hdparm** comes from the package **hdparm**.  You can use it to get/set the IDE SATA parameters. Do not set any parameter before you learn what that does to your system. In the following example, we are assuming /dev/sda as your hard disk. You can replace it with the name of the storage device as you see in the output of **df** command in your system.

     /sbin/hdparm -Tt /dev/sda
     /sbin/hdparm -v /dev/sda

### iostat
The program **iostat** comes from the package **sysstat**. This tool is to report CPU and I/O statistics. In the example below we are assuming that /dev/sda is the storage device in your machine. Change it to what you see in the output of **df** command in your system.

     /usr/bin/iostat -dx /dev/sda

## Configurations

### ifconfig 
This tool comes from the package **net-tools**. The output is about the configuration of network interfaces in your computer.

      /sbin/ifconfig

## Home work

1. Make a listing of the hard ware components you have in your laptop.

2. Look up internet and identify other variants or models of each of the hardware components. Critically compare the specs with the ones you have in your machine in a tabular fashion.

3. List the CPU and GPU capabilities of your machine in GigaFlops as per theoretical or vendor provided specs. You don't have to do any benchmarking yourself for this information.

4. Count the number of packages installed on your OS.

5. Find out the difference in the IP configuration of your machine when you connect your laptop using wired LAN in the hostel room and over WiFi using IITMWiFi.
