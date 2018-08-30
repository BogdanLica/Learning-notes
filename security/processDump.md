* reserach on .dmp file:
    * a dump file is a snapshot of the app at the point in time when the dump is taken
    * it shows: what process was executing and the modules loaded
    * if the dump file has the heaps saved, the content of the memory is saved as well(the value of the variables at the time when the dump was created)
* Start radare2 on the file
* find the OS that was attacked: Windows NT Server Domain Controller
  > i
* to find the process that was used: System32_services.exe
  > iSq~exe
* research on hunting memory:
    * common forms of memory resident malware
        * shellcode injection
            1. OpenProcess(open a target process)
            2. VirtualAllocEx(allocate a chunk of memory in the process)
            3. WriteProcessMemory(write the shellcode payload to the newly allocated section)
            4. CreateRemoteThread(create a new thread in the remote process to execute the shellcode)
        * reflective DLL injection
            * create a DLL that maps itself when executed instead of using the Window's loader
            * the injection process is the same as for the shellcode injection, but instead of the sellcode payload, a self-mapping DLL is used
            * eg. Meterpreter uses it
            * hunt it down: it uses large RWX memory sections, even when the meterpreter session is closed and usually has a function called "ReflectiveLoader()"
        * memory module
            * simmilary to a reflective DLL injection, but the target DLL is mapped instead of the DLL mapping itself
            * load a DLL completely from memory, without storing it on the disk first
        * process hollowing
            1. a process is created in a suspended state
            2. unmapping the original executable from the process
            3. allocate and write a new payload to the process
            4. redirect the execution of the oriinal thread to the new payload(SetThreadContext)
            5. call ResumeThread to continue
        * module hollowing
            * mapping an unused module into a target process and then overwrite the module with its own payload
        * Gargoyle(ROP/APC)
            * [Reading](https://jlospinoso.github.io/security/assembly/c/cpp/developing/software/2017/03/04/gargoyle-memory-analysis-evasion.html)
    * Resources used:
        * [Hunting Memory](https://www.endgame.com/blog/technical-blog/hunting-memory)
        * [Windows Executable Files](https://en.wikibooks.org/wiki/X86_Disassembly/Windows_Executable_Files)
        * [Process hollwing](https://attack.mitre.org/wiki/Technique/T1093)

* listing the contents of all the registers:
  > dr
