## How to install linux in windows OS
- https://docs.microsoft.com/en-us/windows/wsl/install
- Tutorial : https://docs.microsoft.com/en-us/windows/wsl/setup/environment
- YouTUbe : https://www.youtube.com/watch?v=uWNpXOT-Zbo&list=PLhfrWIlLOoKNMHhB39bh3XBpoLxV3f0V9&index=4
- 
![image](https://user-images.githubusercontent.com/69948118/180627700-46181e67-3c22-4b6a-aae2-27aff83171a4.png)
![image](https://user-images.githubusercontent.com/69948118/180627708-051c0301-35f6-41f8-bc54-41b9526ea271.png)

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
