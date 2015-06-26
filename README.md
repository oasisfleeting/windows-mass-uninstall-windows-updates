# windows-mass-uninstall-windows-updates
#Windows Updates Uninstaller Utility

This utility (scripted in AutoHotKey) allows you to batch uninstall the Windows Updates you want from your system. It does not uninstall Service Packs, so you need to uninstall those manually.  Works in Windows XP, Vista, 7, 8 and 8.1.

##Installation

There's no need to install anything, the executable is portable so you just need to download it and run it. The executable will create a temporal text file in its parent directory while it runs, and it will remove it automatically once it doesn't need it anymore.

## Get a list of installed kind buds. 
``wmic qfe get "HotFixID" /format:table``

## Push your kb into a text file
``wmic qfe list brief /format:texttablewsys > "L:\kindbuds.txt"``

## use your favorite text editor to dump everything from the file except the kb's from the text file. 
``Shift + Alt + Left Mouse Click in notepad++ will let you work in column mode. Or put it in a spreadsheet for easy parsing.``

## Run the wusa uninstaller on each (k)iller (b)owl.
``wusa.exe /kb:279503 /uninstall /quiet /norestart``

can't run multiple uninstalls at once, so use robo or autohotkey to run one at a time.

``RunWaitMany(commands) {
wusa.exe /kb:279509 /uninstall /quiet /norestart
wusa.exe /kb:279508 /uninstall /quiet /norestart
wusa.exe /kb:279507 /uninstall /quiet /norestart
wusa.exe /kb:279506 /uninstall /quiet /norestart
wusa.exe /kb:279505 /uninstall /quiet /norestart
}``
