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


