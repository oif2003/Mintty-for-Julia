# Mintty-for-Julia
AutoHotkey script that starts Julia 1.3.1 (64bit) through Mintty 3.0.2 (64bit).  CTRL+C without exiting Julia.

# Prerequisite:  
Must have 64bit Julia 1.3.1 installed at default location, ie: C:\Users\YourUserName\AppData\Local\Julia-1.3.1\bin\julia.exe

# How to Use:  
Unzip file and run mintty4julia.exe to start.  The file is zipped because I included all the Windows emojis (about 3000 of them!).  Mintty should be configured to display them properly.

# How it Works:
mintty4julia.exe is autohotkey v2 binary renamed so it starts mintty4julia.ahk automatically.
If you have doubts you can download AutoHotkey version 2.0-a108-a2fa0498 from https://www.autohotkey.com/
and run the script with the 64bit version of AutoHotkey v2.

This script hides the extra Mintty window that is spawned when Julia is started via the command line with:
"mintty %PATH_OF_JULIA%\julia.exe"
Whenever you hit CTRL+C while the Julia window is in focus, it intercepts it and sends CTRL+C to the hidden Mintty window.
The scripts determines whether Julia is executing a script or not by reading the byte at memory address 0x1004AA3C8 of the mintty host.
This is done because if CTRL+C is sent while Julia is not executing a script, it will cause an error resulting in Julia exiting.
So basically, if Julia is not doing anything, CTRL+C will also do nothing.
