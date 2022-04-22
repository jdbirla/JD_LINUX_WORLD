# Linux World

## Linux High level understanding

![Browser](Images/Screenshot_01.png)
![Browser](Images/Screenshot_02.png)
![Browser](Images/Screenshot_03.png)
![Browser](Images/Screenshot_04.png)
![Browser](Images/Screenshot_05.png)
![Browser](Images/Screenshot_06.png)
![Browser](Images/Screenshot_07.png)
![Browser](Images/Screenshot_08.png)
![Browser](Images/Screenshot_09.png)
![Browser](Images/Screenshot_10.png)
![Browser](Images/Screenshot_11.png)
![Browser](Images/Screenshot_12.png)
![Browser](Images/Screenshot_13.png)
![Browser](Images/Screenshot_14.png)
![Browser](Images/Screenshot_15.png)
![Browser](Images/Screenshot_16.png)
![Browser](Images/Screenshot_17.png)

<pre><font color="#4E9A06"><b>jdublnx@JDUBUNTO</b></font>:<font color="#3465A4"><b>~</b></font>$ cd Documents/
<font color="#4E9A06"><b>jdublnx@JDUBUNTO</b></font>:<font color="#3465A4"><b>~/Documents</b></font>$ ls
file1.txt
<font color="#4E9A06"><b>jdublnx@JDUBUNTO</b></font>:<font color="#3465A4"><b>~/Documents</b></font>$ cat file1.txt 
total 100
drwxr-xr-x 16 jdublnx jdublnx 4096  4月 22 11:15 .
drwxr-xr-x  3 root    root    4096  4月 21 14:04 ..
drwxr-xr-x 13 jdublnx jdublnx 4096  4月 21 16:11 .cache
drwx------ 11 jdublnx jdublnx 4096  4月 21 14:25 .config
drwxr-xr-x  2 jdublnx jdublnx 4096  4月 22 09:25 Desktop
drwxr-xr-x  2 jdublnx jdublnx 4096  4月 22 11:25 Documents
drwxr-xr-x  2 jdublnx jdublnx 4096  4月 21 14:13 Downloads
drwx------  3 jdublnx jdublnx 4096  4月 21 14:14 .gnupg
drwxr-xr-x  3 jdublnx jdublnx 4096  4月 21 14:13 .local
drwx------  4 jdublnx jdublnx 4096  4月 21 14:19 .mozilla
drwxr-xr-x  2 jdublnx jdublnx 4096  4月 21 14:13 Music
drwxr-xr-x  2 jdublnx jdublnx 4096  4月 21 14:13 Pictures
drwxr-xr-x  2 jdublnx jdublnx 4096  4月 21 14:13 Public
drwx------  2 jdublnx jdublnx 4096  4月 21 14:14 .ssh
drwxr-xr-x  2 jdublnx jdublnx 4096  4月 21 14:13 Templates
drwxr-xr-x  2 jdublnx jdublnx 4096  4月 21 14:13 Videos
-rw-r--r--  1 jdublnx jdublnx 3771  4月 21 14:04 .bashrc
-rw-rw-rw-  1 jdublnx jdublnx 1929  4月 22 11:15 Install_CentOS_in_VM.md
-rw-r--r--  1 jdublnx jdublnx  807  4月 21 14:04 .profile
-rw-------  1 jdublnx jdublnx  378  4月 22 09:47 .bash_history
-rw-r--r--  1 jdublnx jdublnx  220  4月 21 14:04 .bash_logout
-rw-r-----  1 jdublnx jdublnx    5  4月 22 09:12 .vboxclient-clipboard.pid
-rw-r-----  1 jdublnx jdublnx    5  4月 22 09:12 .vboxclient-display-svga-x11.pid
-rw-r-----  1 jdublnx jdublnx    5  4月 22 09:12 .vboxclient-draganddrop.pid
-rw-r-----  1 jdublnx jdublnx    5  4月 22 09:12 .vboxclient-seamless.pid
-rw-r--r--  1 jdublnx jdublnx    0  4月 21 14:17 .sudo_as_admin_successful
<font color="#4E9A06"><b>jdublnx@JDUBUNTO</b></font>:<font color="#3465A4"><b>~/Documents</b></font>$ cat &gt; file2.txt
hi my name is jd
welcome to linux world 
<font color="#4E9A06"><b>jdublnx@JDUBUNTO</b></font>:<font color="#3465A4"><b>~/Documents</b></font>$ cat file2.txt 
hi my name is jd
welcome to linux world
<font color="#4E9A06"><b>jdublnx@JDUBUNTO</b></font>:<font color="#3465A4"><b>~/Documents</b></font>$ cat file1.txt 
total 100
drwxr-xr-x 16 jdublnx jdublnx 4096  4月 22 11:15 .
drwxr-xr-x  3 root    root    4096  4月 21 14:04 ..
drwxr-xr-x 13 jdublnx jdublnx 4096  4月 21 16:11 .cache
drwx------ 11 jdublnx jdublnx 4096  4月 21 14:25 .config
drwxr-xr-x  2 jdublnx jdublnx 4096  4月 22 09:25 Desktop
drwxr-xr-x  2 jdublnx jdublnx 4096  4月 22 11:25 Documents
drwxr-xr-x  2 jdublnx jdublnx 4096  4月 21 14:13 Downloads
drwx------  3 jdublnx jdublnx 4096  4月 21 14:14 .gnupg
drwxr-xr-x  3 jdublnx jdublnx 4096  4月 21 14:13 .local
drwx------  4 jdublnx jdublnx 4096  4月 21 14:19 .mozilla
drwxr-xr-x  2 jdublnx jdublnx 4096  4月 21 14:13 Music
drwxr-xr-x  2 jdublnx jdublnx 4096  4月 21 14:13 Pictures
drwxr-xr-x  2 jdublnx jdublnx 4096  4月 21 14:13 Public
drwx------  2 jdublnx jdublnx 4096  4月 21 14:14 .ssh
drwxr-xr-x  2 jdublnx jdublnx 4096  4月 21 14:13 Templates
drwxr-xr-x  2 jdublnx jdublnx 4096  4月 21 14:13 Videos
-rw-r--r--  1 jdublnx jdublnx 3771  4月 21 14:04 .bashrc
-rw-rw-rw-  1 jdublnx jdublnx 1929  4月 22 11:15 Install_CentOS_in_VM.md
-rw-r--r--  1 jdublnx jdublnx  807  4月 21 14:04 .profile
-rw-------  1 jdublnx jdublnx  378  4月 22 09:47 .bash_history
-rw-r--r--  1 jdublnx jdublnx  220  4月 21 14:04 .bash_logout
-rw-r-----  1 jdublnx jdublnx    5  4月 22 09:12 .vboxclient-clipboard.pid
-rw-r-----  1 jdublnx jdublnx    5  4月 22 09:12 .vboxclient-display-svga-x11.pid
-rw-r-----  1 jdublnx jdublnx    5  4月 22 09:12 .vboxclient-draganddrop.pid
-rw-r-----  1 jdublnx jdublnx    5  4月 22 09:12 .vboxclient-seamless.pid
-rw-r--r--  1 jdublnx jdublnx    0  4月 21 14:17 .sudo_as_admin_successful
<font color="#4E9A06"><b>jdublnx@JDUBUNTO</b></font>:<font color="#3465A4"><b>~/Documents</b></font>$ cat file1.txt file2.txt 
total 100
drwxr-xr-x 16 jdublnx jdublnx 4096  4月 22 11:15 .
drwxr-xr-x  3 root    root    4096  4月 21 14:04 ..
drwxr-xr-x 13 jdublnx jdublnx 4096  4月 21 16:11 .cache
drwx------ 11 jdublnx jdublnx 4096  4月 21 14:25 .config
drwxr-xr-x  2 jdublnx jdublnx 4096  4月 22 09:25 Desktop
drwxr-xr-x  2 jdublnx jdublnx 4096  4月 22 11:25 Documents
drwxr-xr-x  2 jdublnx jdublnx 4096  4月 21 14:13 Downloads
drwx------  3 jdublnx jdublnx 4096  4月 21 14:14 .gnupg
drwxr-xr-x  3 jdublnx jdublnx 4096  4月 21 14:13 .local
drwx------  4 jdublnx jdublnx 4096  4月 21 14:19 .mozilla
drwxr-xr-x  2 jdublnx jdublnx 4096  4月 21 14:13 Music
drwxr-xr-x  2 jdublnx jdublnx 4096  4月 21 14:13 Pictures
drwxr-xr-x  2 jdublnx jdublnx 4096  4月 21 14:13 Public
drwx------  2 jdublnx jdublnx 4096  4月 21 14:14 .ssh
drwxr-xr-x  2 jdublnx jdublnx 4096  4月 21 14:13 Templates
drwxr-xr-x  2 jdublnx jdublnx 4096  4月 21 14:13 Videos
-rw-r--r--  1 jdublnx jdublnx 3771  4月 21 14:04 .bashrc
-rw-rw-rw-  1 jdublnx jdublnx 1929  4月 22 11:15 Install_CentOS_in_VM.md
-rw-r--r--  1 jdublnx jdublnx  807  4月 21 14:04 .profile
-rw-------  1 jdublnx jdublnx  378  4月 22 09:47 .bash_history
-rw-r--r--  1 jdublnx jdublnx  220  4月 21 14:04 .bash_logout
-rw-r-----  1 jdublnx jdublnx    5  4月 22 09:12 .vboxclient-clipboard.pid
-rw-r-----  1 jdublnx jdublnx    5  4月 22 09:12 .vboxclient-display-svga-x11.pid
-rw-r-----  1 jdublnx jdublnx    5  4月 22 09:12 .vboxclient-draganddrop.pid
-rw-r-----  1 jdublnx jdublnx    5  4月 22 09:12 .vboxclient-seamless.pid
-rw-r--r--  1 jdublnx jdublnx    0  4月 21 14:17 .sudo_as_admin_successful
hi my name is jd
welcome to linux world
<font color="#4E9A06"><b>jdublnx@JDUBUNTO</b></font>:<font color="#3465A4"><b>~/Documents</b></font>$ cat file1.txt &gt;&gt; file2.txt 
<font color="#4E9A06"><b>jdublnx@JDUBUNTO</b></font>:<font color="#3465A4"><b>~/Documents</b></font>$ cat file2.txt 
hi my name is jd
welcome to linux world
total 100
drwxr-xr-x 16 jdublnx jdublnx 4096  4月 22 11:15 .
drwxr-xr-x  3 root    root    4096  4月 21 14:04 ..
drwxr-xr-x 13 jdublnx jdublnx 4096  4月 21 16:11 .cache
drwx------ 11 jdublnx jdublnx 4096  4月 21 14:25 .config
drwxr-xr-x  2 jdublnx jdublnx 4096  4月 22 09:25 Desktop
drwxr-xr-x  2 jdublnx jdublnx 4096  4月 22 11:25 Documents
drwxr-xr-x  2 jdublnx jdublnx 4096  4月 21 14:13 Downloads
drwx------  3 jdublnx jdublnx 4096  4月 21 14:14 .gnupg
drwxr-xr-x  3 jdublnx jdublnx 4096  4月 21 14:13 .local
drwx------  4 jdublnx jdublnx 4096  4月 21 14:19 .mozilla
drwxr-xr-x  2 jdublnx jdublnx 4096  4月 21 14:13 Music
drwxr-xr-x  2 jdublnx jdublnx 4096  4月 21 14:13 Pictures
drwxr-xr-x  2 jdublnx jdublnx 4096  4月 21 14:13 Public
drwx------  2 jdublnx jdublnx 4096  4月 21 14:14 .ssh
drwxr-xr-x  2 jdublnx jdublnx 4096  4月 21 14:13 Templates
drwxr-xr-x  2 jdublnx jdublnx 4096  4月 21 14:13 Videos
-rw-r--r--  1 jdublnx jdublnx 3771  4月 21 14:04 .bashrc
-rw-rw-rw-  1 jdublnx jdublnx 1929  4月 22 11:15 Install_CentOS_in_VM.md
-rw-r--r--  1 jdublnx jdublnx  807  4月 21 14:04 .profile
-rw-------  1 jdublnx jdublnx  378  4月 22 09:47 .bash_history
-rw-r--r--  1 jdublnx jdublnx  220  4月 21 14:04 .bash_logout
-rw-r-----  1 jdublnx jdublnx    5  4月 22 09:12 .vboxclient-clipboard.pid
-rw-r-----  1 jdublnx jdublnx    5  4月 22 09:12 .vboxclient-display-svga-x11.pid
-rw-r-----  1 jdublnx jdublnx    5  4月 22 09:12 .vboxclient-draganddrop.pid
-rw-r-----  1 jdublnx jdublnx    5  4月 22 09:12 .vboxclient-seamless.pid
-rw-r--r--  1 jdublnx jdublnx    0  4月 21 14:17 .sudo_as_admin_successful
<font color="#4E9A06"><b>jdublnx@JDUBUNTO</b></font>:<font color="#3465A4"><b>~/Documents</b></font>$ ^C
</pre>