# Diagnose an infected machine

### Keep in mind
* anomalous processes running
* how many instances of native windows programs do I expect to see running
* any strange external connections
* any process beaconing outbound that should not be
* which libraries are being imported by each process
* any malicious drivers
* any injected code into anomalous processes


### Learning about Volatility

###### Analysis on an infected machine



* first we need to identify the OS from where the memory dump was taken
  > imageinfo
* let's find the running processes at the time the memory dump was taken
  > pslist
* anomalous processes running:
    * lsass.exe(3 instances of it, none of them were closed before another one started)
    * svchost.exe(5 instances of it)
    * imapi.exe(is it in C:\Windows\System32  ???)
    * jusched.exe(is it installed in program files\common files ???)
    * wuauclt.exe(is it in a temporary folder/user profile folder/ in C:\ or C\Windows etc ??? The true location is C:\Windows\System32 )
    * procmon.exe(a thread if it is in C:\Windows or System32 folder)
    * wmiprvse.exe(same , a Microsoft product)
    * cmd.exe
    * ipconfig

* libraries used(DLLs):
    * most have a system32 folder, there are some with System32
    * \pchealth\helpctr\binaries\pchsvc.dll

* by looking at the processes in a tree format, by best guess that the problem has started from the running of the explorer.exe
  > pstree
* by looking at the clipboard, a suspicious executable can be indentified:74ddc49a7c121a61b8d06c03f92d0c13.exe
* scanning through the file and using grep, the same suspicious file can be identified
  > grep -E [0-9][A-Za-z0-9]*.exe
* using the timeliner:
  * at the end, suspicious files were ran: chmod.exe,bash.exe,mound.exe,sh.exe
  *  idapro_931_42287435c1a6ed5a6d6039345b7c49c2.exe
* looking at environmental variables:
  > envars
  * TurtoiseSVN qq
