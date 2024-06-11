# Linux in windows

# Table of contents
- [Linux in windows](#linux-in-windows)
  - [How to install linux in windows OS](#how-to-install-linux-in-windows-os)
    - [Access windows os files into linux](#access-windows-os-files-into-linux)
    - [How to change password in wsl](#how-to-change-password-in-wsl)
    - [Access linux files from windows files system](#access-linux-files-from-windows-files-system)
    - [Windows Terminal](#windows-terminal)
    - [Run Linux GUI apps on the Windows Subsystem for Linux](#run-linux-gui-apps-on-the-windows-subsystem-for-linux)
    - [WSL 2 Networking](#wsl-2-networking)
  - [How to create Dev env in wsl](#how-to-create-dev-env-in-wsl)
    - [Can we use application from windows to wsl](#can-we-use-application-from-windows-to-wsl)
    - [How to use intellij in WSl](#how-to-use-intellij-in-wsl)
    - [Git ssh](#git-ssh)
  - [GUI in linux](#gui-in-linux)
  - [How to work in WSL from Local Intellij and use Java Project from WSL](#how-to-work-in-wsl-from-local-intellij-and-use-java-project-from-wsl)
    - [Install Java in wsl](#install-java-in-wsl)
    - [Remove home path from windows](#remove-home-path-from-windows)
    - [Install maven in WSL](#install-maven-in-wsl)
    - [Set Intellij](#set-intellij)
  - [How to work in WSL use intellij also from wsl](#how-to-work-in-wsl-use-intellij-also-from-wsl)
    - [Check arch type for linux machine](#check-arch-type-for-linux-machine)
    - [Goto intellij site and download community version for linux X86_64](#goto-intellij-site-and-download-community-version-for-linux-x86_64)
    - [Move that tar file in wsl dir](#move-that-tar-file-in-wsl-dir)
    - [unzip that file and move to /opt](#unzip-that-file-and-move-to-opt)
    - [Create symbolic link](#create-symbolic-link)
    - [you can use now](#you-can-use-now)
    - [It will open intellij](#it-will-open-intellij)
  - [AWS CLI COnfiguration](#aws-cli-configuration)
  - [Installing docker in WSl2 without Docker desktop no license required](#installing-docker-in-wsl2-without-docker-desktop-no-license-required)
 
  
## How to install linux in windows OS
- https://docs.microsoft.com/en-us/windows/wsl/install
- Tutorial : https://docs.microsoft.com/en-us/windows/wsl/setup/environment
- YouTUbe : https://www.youtube.com/watch?v=uWNpXOT-Zbo&list=PLhfrWIlLOoKNMHhB39bh3XBpoLxV3f0V9&index=4
- 
![image](https://user-images.githubusercontent.com/69948118/180627700-46181e67-3c22-4b6a-aae2-27aff83171a4.png)
![image](https://user-images.githubusercontent.com/69948118/180627708-051c0301-35f6-41f8-bc54-41b9526ea271.png)
- https://jensknipper.de/blog/using-maven-in-wsl/

### Access windows os files into linux
- user: jdwinlinux
- pass: jdwinlinux

### How to change password in wsl
https://www.jamestharpe.com/wsl-root-password/#:~:text=Open%20PowerShell%2C%20then%20use%20the,your%20password%20twice%20as%20prompted.

```sh
jdwinlinux@DESKTOP-AS2FQOH:~/jddocs$ cd /mnt/c/
jdwinlinux@DESKTOP-AS2FQOH:/mnt/c$ ls
ls: cannot access 'DumpStack.log.tmp': Permission denied
ls: cannot access 'hiberfil.sys': Permission denied
ls: cannot access 'pagefile.sys': Permission denied
ls: cannot access 'swapfile.sys': Permission denied
'$Recycle.Bin'             DumpStack.log.tmp   PerfLogs                     Users          pagefile.sys
'$WinREAgent'              Gradle             'Program Files'               Windows        selenium
 AVScanner.ini             JD_Google_Drive    'Program Files (x86)'         app            swapfile.sys
 C_Drive                   Kompose             ProgramData                  gh             xampp
 D_Drive                   OD                  Recovery                     hiberfil.sys
'Documents and Settings'   OneDriveTemp       'System Volume Information'   kubectl
jdwinlinux@DESKTOP-AS2FQOH:/mnt/c$ cd D_Drive/
jdwinlinux@DESKTOP-AS2FQOH:/mnt/c/D_Drive$ ls
DXC  Job_Switch  Kirti  Personal  jdk-11.0.10_windows-x64_bin.exe  react
jdwinlinux@DESKTOP-AS2FQOH:/mnt/c/D_Drive$
```

### Access linux files from windows files system
- used comman from linux terminal " explorer.exe . Winfows file system : \\wsl$\Ubuntu\home\jdwinlinux

---
### Windows Terminal
![image](https://user-images.githubusercontent.com/69948118/180634720-53037c82-826f-48f3-9ebe-bb9d170d4a70.png)
![image](https://user-images.githubusercontent.com/69948118/180634753-6ddfe1fd-368c-4be5-93d4-480997805243.png)

---
### Run Linux GUI apps on the Windows Subsystem for Linux
!Ubuntu GUI commands:
sudo apt update && sudo apt -y upgrade
sudo apt-get purge xrdp
sudo apt install -y xrdp
sudo apt install -y xfce4
sudo apt install -y xfce4-goodies


sudo cp /etc/xrdp/xrdp.ini /etc/xrdp/xrdp.ini.bak
sudo sed -i 's/3389/3390/g' /etc/xrdp/xrdp.ini
sudo sed -i 's/max_bpp=32/#max_bpp=32\nmax_bpp=128/g' /etc/xrdp/xrdp.ini
sudo sed -i 's/xserverbpp=24/#xserverbpp=24\nxserverbpp=128/g' /etc/xrdp/xrdp.ini
echo xfce4-session > ~/.xsession

sudo nano /etc/xrdp/startwm.sh
!comment these lines to:
#test -x /etc/X11/Xsession && exec /etc/X11/Xsession
#exec /bin/sh /etc/X11/Xsession

!add these lines:
# xfce
startxfce4

sudo /etc/init.d/xrdp start

!Now in Windows, use Remote Desktop Connection
localhost:3390

!Then login using your Ubuntu username and password

---

### WSL 2 Networking
----
## How to create Dev env in wsl
### Can we use application from windows to wsl 
Yes, you can access and use the software and tools installed in the Windows file system from within WSL. When you install WSL, it provides a mechanism for integrating the Windows file system with the Linux environment.

By default, the Windows file system is mounted under the `/mnt` directory in WSL. This means you can access your Windows drives and files from within WSL. For example, your `C:` drive will be available at `/mnt/c/` in WSL.

To use software or tools installed in the Windows file system within WSL, you have a couple of options:

1. Use the Windows executable directly: If you have software installed in Windows, such as Git or Maven, you can execute them from the WSL command line by specifying the full path to the executable. For example, you can run `C:\Path\To\Git\git` or `C:\Path\To\Maven\mvn` from within WSL.

2. Add Windows executable path to WSL's PATH: If you want to use Windows executables without specifying the full path every time, you can add the Windows executable directory to the PATH environment variable in WSL. This way, you can simply run the commands by their names. To do this, you'll need to edit the `~/.bashrc` or `~/.bash_profile` file in WSL and add the following line:

   ```
   export PATH=$PATH:/mnt/c/Path/To/Executable
   ```

   Replace `/mnt/c/Path/To/Executable` with the actual path to the directory containing the executables you want to use. After saving the file, you'll need to restart your WSL session or run `source ~/.bashrc` or `source ~/.bash_profile` for the changes to take effect.

By leveraging these approaches, you can seamlessly use software and tools installed in the Windows file system within your WSL Linux environment.

### When I execute 'java --version' in wsl I can see corretto-11 while checking using above command from $PATH , the java path is `/mnt/c/Program Files/Java/jdk-17.0.5/bin` , I don't understand this, Why I can see java 11 not java 17
The situation you described suggests that there might be multiple Java versions installed on your system, and the one being executed when you run `java --version` in WSL is not the same as the one listed in the `/mnt/c/Program Files/Java/jdk-17.0.5/bin` path.

When you run `java --version` in WSL, it searches for the executable in the directories listed in the `$PATH` variable in the order they are specified. It stops at the first occurrence of `java` that it finds.

To determine why you are seeing Java 11 instead of Java 17, you can check the following:

1. Check the order of directories in the `$PATH` variable. Run `echo $PATH` in WSL to verify the order of directories. If the directory containing the Java 11 executable appears before the one containing Java 17, then that could be the reason why Java 11 is being picked up.

2. Verify if there are any symbolic links or aliases set up for the `java` command. It's possible that there is a symbolic link or an alias pointing to the Java 11 executable, even though the `$PATH` variable points to Java 17. You can check this by running `ls -l /usr/bin/java` in WSL to see if it is pointing to a different location.

3. Ensure that you are running the `java --version` command from within WSL and not from a Windows command prompt or PowerShell. The behavior of the `java` command may differ depending on the environment from which it is executed.

By investigating these aspects, you should be able to determine why Java 11 is being displayed when running `java --version` in WSL, despite having Java 17 listed in the `$PATH` variable.

### you mean if I have docker install in windows I can access docker inside wsl without insalling docker in wsl
Yes, that's correct. If you have Docker Desktop installed on your Windows system, you can access and use Docker from within WSL without needing to install Docker separately inside WSL.

Here's how it works:

1. Install Docker Desktop: Ensure that you have Docker Desktop installed and running on your Windows system. Docker Desktop includes the necessary components to run Docker containers both in Windows and within WSL.

2. Enable WSL Integration: In Docker Desktop settings, you can enable the WSL integration feature. This establishes a connection between Docker running in Windows and the WSL distribution of your choice.

3. Run Docker Commands in WSL: Once the WSL integration is enabled, you can open a WSL terminal and use Docker commands just like you would in a Linux environment. Docker commands executed within WSL will be executed in the Docker engine running in Windows, but the containers themselves will run within the WSL environment.

This integration allows you to seamlessly work with Docker containers from both Windows and WSL, using the same Docker installation. You can build, run, and manage containers from either environment without the need for duplicate installations or configurations.

By leveraging Docker Desktop's integrated support for WSL, you can maintain a unified Docker experience and avoid potential conflicts or inconsistencies that might arise from separately installing Docker within WSL.

### How to use intellij in WSl
- https://www.jetbrains.com/help/idea/how-to-use-wsl-development-environment-in-product.html#debugging_system_settings
- trouble shooting  : https://stackoverflow.com/questions/67116880/how-to-correctly-set-up-intellij-with-wsl2


### Git ssh
- https://docs.github.com/en/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent
- https://docs.github.com/en/get-started/getting-started-with-git/about-remote-repositories
----
## GUI in linux
 - https://medium.com/javarevisited/using-wsl-2-with-x-server-linux-on-windows-a372263533c3
 - As of my knowledge cutoff in September 2021, WSL2 (Windows Subsystem for Linux) does not have built-in support for running graphical user interface (GUI) applications directly on Windows. WSL2 is primarily designed for command-line and server-based applications.

However, there are some workarounds to enable GUI applications in WSL2 by using an X server on Windows. Here's a step-by-step guide on how to set up a graphical environment for WSL2:

1. Install an X server on Windows:
   To enable GUI applications in WSL2, you need to install an X server on your Windows machine. One popular option is Xming (https://sourceforge.net/projects/xming/). Download and install the Xming X Server on your Windows system.

2. Set the DISPLAY environment variable in WSL2:
   In your WSL2 terminal, set the `DISPLAY` environment variable to point to your Windows machine's IP address and the display number. Replace `<Windows_IP>` with your actual Windows machine's IP address. You can find your IP address by running `ipconfig` in a Windows Command Prompt or PowerShell.
   ```
   export DISPLAY=<Windows_IP>:0.0
   ```

3. Install GUI packages in WSL2:
   You will need to install necessary GUI packages in your WSL2 distribution. For example, you can install a lightweight desktop environment like XFCE4 along with other required components:
   ```
   sudo apt update
   sudo apt install xfce4 xfce4-goodies x11-apps
   ```

4. Run Xming on Windows:
   Start the Xming X Server on your Windows machine. Make sure it is running and ready to accept connections.

5. Test the GUI application:
   You can now test if GUI applications work in WSL2. For example, you can run the `xfce4-session` command to start the XFCE desktop environment:
   ```
   xfce4-session
   ```

   The GUI applications launched from within WSL2 should now be displayed on your Windows desktop through the X server.

Please note that running GUI applications in WSL2 using an X server can have limitations and performance considerations. It is not a native or fully optimized solution, so complex or graphics-intensive applications may not work as expected.

Always remember to check for the latest developments and improvements related to GUI support in WSL2, as Microsoft may introduce new features or changes in future updates. Additionally, you can explore alternative solutions like using Windows Subsystem for Linux GUI (WSLg), which aims to provide a more integrated and native experience for running Linux GUI applications in WSL2.

Yes, there are other X servers for Windows that you can use instead of Xming. One popular alternative to Xming is VcXsrv (also known as VcXsrv Windows X Server). VcXsrv provides similar functionality and allows you to run graphical applications from WSL2 and other Linux distributions on your Windows desktop.

Here's how you can use VcXsrv to enable GUI applications in WSL2:

1. Install VcXsrv:
   Download VcXsrv from its GitHub repository (https://sourceforge.net/projects/vcxsrv/). Choose the latest release version and download the installer. Run the installer to install VcXsrv on your Windows machine.

2. Set the DISPLAY environment variable in WSL2:
   In your WSL2 terminal, set the `DISPLAY` environment variable to point to the VcXsrv X server. The default display number for VcXsrv is 0.
   ```
   export DISPLAY=:0
   ```

3. Install GUI packages in WSL2 (if not already installed):
   As mentioned earlier, you may need to install necessary GUI packages in your WSL2 distribution. For example, you can install a lightweight desktop environment like XFCE4 along with other required components:
   ```
   sudo apt update
   sudo apt install xfce4 xfce4-goodies x11-apps
   ```

4. Run VcXsrv on Windows:
   Start the VcXsrv X Server on your Windows machine. You should see the VcXsrv icon in your system tray indicating that it's running and ready to accept connections.

5. Test the GUI application:
   You can now test if GUI applications work in WSL2. For example, you can run the `xfce4-session` command to start the XFCE desktop environment:
   ```
   xfce4-session
   ```

   The GUI applications launched from within WSL2 should now be displayed on your Windows desktop through VcXsrv.

VcXsrv provides additional configuration options that you can explore to customize the X server behavior according to your preferences. Remember to check the VcXsrv documentation and GitHub repository for more information and updates.

As with any X server solution for WSL2, keep in mind that running GUI applications in this manner might have limitations and performance considerations, especially for graphics-intensive applications. For a more integrated and native experience, you can also explore the Windows Subsystem for Linux GUI (WSLg) feature, which aims to provide better support for Linux GUI applications in WSL2.


![image](https://github.com/jdbirla/JD_LINUX_WORLD/assets/69948118/0b82757e-3696-487a-abe4-33696026a549)
![image](https://github.com/jdbirla/JD_LINUX_WORLD/assets/69948118/af9d87f9-0ea2-4907-ab67-4b8d56d903fd)
![image](https://github.com/jdbirla/JD_LINUX_WORLD/assets/69948118/19c95b93-3a2c-4e7c-9e59-29577c5b6d87)
![image](https://github.com/jdbirla/JD_LINUX_WORLD/assets/69948118/297a2572-3010-4ae0-b5ec-ffcb82b31bcf)
![image](https://github.com/jdbirla/JD_LINUX_WORLD/assets/69948118/fdb3f83a-190e-4bf1-8181-a18f8fb62005)

----
## How to work in WSL from Local Intellij and use Java Project from WSL
- https://youtrack.jetbrains.com/issue/IDEA-267333/Maven-wsl-projects-is-failing-to-resolve-dependencies
![image](https://github.com/jdbirla/JD_LINUX_WORLD/assets/69948118/ed996c9c-12b1-47c0-9663-92acb0607d10)

### Install Java in wsl 
```sh
sudo apt update
sudo apt upgrade

sudo apt install openjdk-11-jdk




```
#### Set Java Home Path in .bashrc file and restart the terminal
![image](https://github.com/jdbirla/JD_LINUX_WORLD/assets/69948118/f203e2f9-46b0-4f79-8bfa-8d4d811c5f05)
```sh
jdwinlinux@PSL-21VL6Q3:~$ java --version
openjdk 11.0.19 2023-04-18
OpenJDK Runtime Environment (build 11.0.19+7-post-Ubuntu-0ubuntu122.04.1)
OpenJDK 64-Bit Server VM (build 11.0.19+7-post-Ubuntu-0ubuntu122.04.1, mixed mode, sharing)
jdwinlinux@PSL-21VL6Q3:~$
```
### Remove home path from windows 
```
%Maven_Home%\bin
%JAVA_HOME%\bin
```

### Install maven in WSL
#### Download apche maven from maven official site not from apt package
![image](https://github.com/jdbirla/JD_LINUX_WORLD/assets/69948118/4c2208ee-b0b3-4f5d-ae29-274f24a28d10)
- Unzip this tar and move to /opt folder
```sh
  unzip apache-maven-3.8.8-bin.zip 
sudo mv apache-maven-3.8.8 /opt/
```
#### Set the home path for maven in .profile Don't set maven in .bashrc file
```sh
vim ~/.profile
# Add below lines as per your path in .profile
export M2_HOME=/opt/apache-maven-3.8.8
export PATH="$PATH:$M2_HOME/bin"
mvn --version
```
![image](https://github.com/jdbirla/JD_LINUX_WORLD/assets/69948118/63ae6b96-1d18-4923-8ca1-3811365a1e39)

![image](https://github.com/jdbirla/JD_LINUX_WORLD/assets/69948118/5d77f3d3-3ff4-4e12-8152-4e788c089dab)

### Set Intellij
#### Intellij version used
![image](https://github.com/jdbirla/JD_LINUX_WORLD/assets/69948118/2243d28f-0d32-47a2-a912-ab5356940d1f)

#### Set Java SDK from WSL in project structure
![image](https://github.com/jdbirla/JD_LINUX_WORLD/assets/69948118/e0a576d3-4544-4654-907a-9987f0728f36)
#### Set Maven home path from WSL
![image](https://github.com/jdbirla/JD_LINUX_WORLD/assets/69948118/184ae263-6a86-4a27-a9a8-aafb78d721f1)

#### Set JDK for importer from WSL
![image](https://github.com/jdbirla/JD_LINUX_WORLD/assets/69948118/c95a01f2-7a15-4a96-945c-134943f8a4c0)

---
## How to work in WSL use intellij also from wsl
### Check arch type for linux machine
![image](https://github.com/jdbirla/JD_LINUX_WORLD/assets/69948118/c92a6356-812a-49cf-ad32-29d54581da42)
### Goto intellij site and download community version for linux X86_64
![image](https://github.com/jdbirla/JD_LINUX_WORLD/assets/69948118/9ebeafbb-472b-4130-8517-fddeaeb03022)
### Move that tar file in wsl dir
![image](https://github.com/jdbirla/JD_LINUX_WORLD/assets/69948118/2fc45a61-37f7-4c84-bcc7-018b019feccc)

### unzip that file and move to /opt
```sh
sudo tar -xzf intellij.x.x.x
sudo mv intellij.x.x.x /opt
```
### Create symbolic link
```sh
sudo ln -s /opt/idea-IC-231.9225.16/bin/idea.sh /usr/local/bin/idea
```
### you can use now
` sudo idea`
### It will open intellij
![image](https://github.com/jdbirla/JD_LINUX_WORLD/assets/69948118/19c03424-e09b-48a8-8805-63cc9ca082aa)
![image](https://github.com/jdbirla/JD_LINUX_WORLD/assets/69948118/f15614ff-031c-4fff-ad16-51ea4b6eba8e)
![image](https://github.com/jdbirla/JD_LINUX_WORLD/assets/69948118/81426168-2a08-4ac2-8dd5-048c8402ed76)

---
## AWS CLI COnfiguration
- https://devopscube.com/install-configure-aws-cli-linux/

---
## Installing docker in WSl2 without Docker desktop no license required
- https://dev.to/bowmanjd/install-docker-on-windows-wsl-without-docker-desktop-34m9
- https://nickjanetakis.com/blog/install-docker-in-wsl-2-without-docker-desktop
![image](https://github.com/jdbirla/JD_LINUX_WORLD/assets/69948118/7bb2acfe-52d9-4289-a0c7-68a5a951fc93)

---
## Setup mf-aod for all fund
- If project is closing automatically while oprning then open that project from other intellin from windows.
- second option try open project from idea.sh intellij
![image](https://github.com/jdbirla/JD_LINUX_WORLD/assets/69948118/5a04d7ca-b9ea-47cb-9552-ec49f3e5bc3e)
![image](https://github.com/jdbirla/JD_LINUX_WORLD/assets/69948118/789572d7-35af-450c-8184-5ea5e2ee34c3)
![image](https://github.com/jdbirla/JD_LINUX_WORLD/assets/69948118/ca266f22-392a-4390-b1b4-7b0be3a9cedb)
![image](https://github.com/jdbirla/JD_LINUX_WORLD/assets/69948118/1f34c2be-ebd7-4d70-9f62-57d93476f2e5)

---
## WSL Commands
Windows Subsystem for Linux (WSL) allows you to run a Linux distribution on your Windows machine. Here are some useful WSL commands to manage and use WSL effectively:

### Basic WSL Commands

1. **Launch WSL:**
   ```sh
   wsl
   ```
   This command launches the default WSL distribution.

2. **Launch a Specific Distribution:**
   ```sh
   wsl -d <DistroName>
   ```
   Replace `<DistroName>` with the name of your installed distribution (e.g., Ubuntu, Debian).

3. **List All Installed Distributions:**
   ```sh
   wsl -l -v
   ```
   This command lists all installed WSL distributions along with their version (WSL 1 or WSL 2).

4. **Set Default Distribution:**
   ```sh
   wsl --set-default <DistroName>
   ```
   This sets the specified distribution as the default one to be used when `wsl` is run without arguments.

5. **Set WSL Version:**
   ```sh
   wsl --set-version <DistroName> <Version>
   ```
   Replace `<DistroName>` with your distribution's name and `<Version>` with `1` or `2` to set the WSL version.

6. **Check WSL Version:**
   ```sh
   wsl -l -v
   ```
   This command will show the current version (WSL 1 or WSL 2) for each installed distribution.

7. **Terminate a Distribution:**
   ```sh
   wsl --terminate <DistroName>
   ```
   This command terminates the specified running distribution.

8. **Shutdown WSL:**
   ```sh
   wsl --shutdown
   ```
   This command stops all running WSL distributions and the WSL 2 lightweight utility virtual machine.

9. **Import a Distribution:**
   ```sh
   wsl --import <DistroName> <InstallLocation> <TarFile>
   ```
   Imports a tar file as a new WSL distribution.

10. **Export a Distribution:**
    ```sh
    wsl --export <DistroName> <FileName>
    ```
    Exports the specified distribution to a tar file.

11. **Unregister a Distribution:**
    ```sh
    wsl --unregister <DistroName>
    ```
    Unregisters the specified distribution, deleting all its data.

### Using Linux Commands in WSL

Once you are in the WSL environment, you can use typical Linux commands. Here are some commonly used Linux commands:

1. **Update Package Lists:**
   ```sh
   sudo apt update
   ```

2. **Upgrade Packages:**
   ```sh
   sudo apt upgrade
   ```

3. **Install a Package:**
   ```sh
   sudo apt install <package-name>
   ```

4. **Change Directory:**
   ```sh
   cd /path/to/directory
   ```

5. **List Directory Contents:**
   ```sh
   ls -la
   ```

6. **Copy Files:**
   ```sh
   cp source_file destination_file
   ```

7. **Move or Rename Files:**
   ```sh
   mv old_name new_name
   ```

8. **Remove Files or Directories:**
   ```sh
   rm -rf /path/to/file_or_directory
   ```

9. **Display Current Directory:**
   ```sh
   pwd
   ```

10. **View File Contents:**
    ```sh
    cat filename
    ```

11. **Edit Files with Nano:**
    ```sh
    nano filename
    ```

### Windows and WSL Integration

1. **Access Windows Files from WSL:**
   ```sh
   cd /mnt/c/Users/YourUsername
   ```
   The `C:` drive and other Windows drives are mounted under `/mnt` in WSL.

2. **Run Windows Commands from WSL:**
   ```sh
   explorer.exe .
   ```
   This opens the current directory in Windows File Explorer.

3. **Run Linux Commands from Windows Command Prompt or PowerShell:**
   ```sh
   wsl ls -la
   ```
   This runs the `ls -la` command in the default WSL distribution.

### Networking and WSL

1. **Check IP Address:**
   ```sh
   ip addr
   ```

2. **Ping a Server:**
   ```sh
   ping www.example.com
   ```

3. **Display Network Configuration:**
   ```sh
   ifconfig
   ```

### File Management

1. **Copy Files between Windows and WSL:**
   ```sh
   cp /mnt/c/Users/YourUsername/file.txt /home/youruser/
   cp /home/youruser/file.txt /mnt/c/Users/YourUsername/
   ```

By using these commands, you can effectively manage and use WSL on your Windows machine.

