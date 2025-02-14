## VIM OR VI #vim

vi index.html


Command Mode and Insert Mode

Command you can read and insert you can edit.

Command is for moving around with arrow keys.

**X** -delete
**dd** -delete the entire line
**yy** -copy the entire line
**p** -paste the line
**ctrl+u or ctrl+d** -scroll up and down

**:** -takes you to the prompt to type commands
**:W** -save or 
**:W filename** -save file
**:q** -quit or discard
**:wq** -save changes and quit

**/of** -find all occurrences of a string and hit **"n"** to move to next



## Misc Linux Commands #linux

**whoami** - print current user

**id** - give more information about current user, to include groups, uid, etc.

**su** "username" - switch user to different user

**ssh username@host** - self explanatory


**ls /root** - permission denied 

**sudo ls /root** - grants the user access and writes an entry to the /etc/sudoers file


### Download Files

**curl http://www.some-site.com/some-file.txt -O** 

**wget http://www.some-site.com/some-file.txt -O some-file.txt


### Get Current OS

**ls /etc/'release'** - lists files in OS directory

**cat /etc/'release'** - read the file of your choosing from the release folder i.e. 



## Redhat RPM (Red Hat Package Manager) #redhat


**rpm -i telnet.rpm** - Install telnet package

**rpm -e telnet** - Uninstall telnet package

**rpm -q telnet** - Query Package


Note: RPM does not take care of other dependent libraries. I.e. Installing Ansible via RPM would not find python and other dependencies.

## YUM #yum

Yum is a package manager that is a high level tool that uses RPM underneath the hood.

Yum searches software repos and installs all the dependencies. These repos can be local or publicly found warehouses with all of the embedded tools. Yum installs the package you want and all of the dependencies in the order required.

**yum install ansible** - install the package with all dependencies in the specific order that is required

The /etc/yum.repos.d file specifies all of the dependencies and order required for each package to work when utilizing Yum.

Sometimes you will need to configure additional repos for Yum to be able to find those packages.

**yum repolist** - this command shows the yum repos with available packages on your system

**ls /etc/yum.repos.d/** - show all the files under the yum repos directory

**cat /etc/yum.repos.d/CentOS-Base.repo** - this will show you the list of the files and links that are contained in the package

![[Pasted image 20240801201343.png]]

**yum list ansible** - lists installed packages and available packages

**yum remove ansible** - this removes the package from the machine

**yum --showduplicates list ansible** - show all available packages and where they are contained

**yum install ansible-2.4.2.0** - installs the specific version of the package you specified

![[Pasted image 20240801201512.png]]



### For figuring out current OS utilized

Look at the **/etc/os-release** file.

