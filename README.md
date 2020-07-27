# Arbitrary Delete to System Primitive

*This is just the implementation of the technique which has been described by @jonasLyk in the following url: https://secret.club/2020/04/23/directory-deletion-shell.html . So all the gr33tz goes to JonasL*

1. When you initialize the class, you can pass as an argument the folder you want to create. If you pass no arguments, the "c:\windows\system32\wermgr.exe.local" will be used.

2. You can call the create_target_folder, in order to create the folder which you passed during the initialization of the class.

3. You can call the escalateToSystem which receives as an argument a dll file. This dll will be executed as SYSTEM. In the pre-compiled folder you will find the dll which is being provided by Jonas_L in his writeup. This function is used in the example file "Delete.cpp"

**This class abuses an arbitrary delete primitive. This means, that it is your responsibility to find a way and delete the C:\ProgramData\Microsoft\Windows\WER .**

In order for this primitive to work **you must to delete the C:\ProgramData\Microsoft\Windows\WER before using this class.**

### Change Log
I changed escalateToSystem, and now the function uses the CompatTelRunner in order to support escalation in Windows 10 Pro systems. 

For windows Home, it will use wermgr.exe.local, as described by Jona_L .
