# Arbitrary Delete to System Primitive

*This is just the implementation of the technique which has been described by @jonasLyk in the following url: https://secret.club/2020/04/23/directory-deletion-shell.html . So all the gr33tz goes to JonasL*

1. When you initialize the class, you can pass as an argument the folder you want to create. If you pass no arguments, the "c:\windows\system32\wermgr.exe.local" will be used.

2. You can call the create_target_folder, in order to create the folder which you passed during the initialization of the class.

3. You can call the escalateToSystem which receives as an argument a dll file. This dll will be executed as SYSTEM. In the pre-compiled folder you will find the dll which is being provided by Jonas in his writeup. This function is used in the example file "Delete.cpp"

**This class abuses an arbitrary delete primitive. This means, that it is your responsibility to find a way and delete the C:\ProgramData\Microsoft\Windows\WER .**

In order for this primitive to work **you must to delete the C:\ProgramData\Microsoft\Windows\WER before using this class.**

### Note
Based on my tests, this technique (as is) can create an abritrary folder (create_target_folder) in some windows versions. Maybe it can create_target_folder in all Windows versions, but I have not tested it in every version.

However, regarding the escalateToSystem it has been succesfully tested only against Windows Home Edition . It seems that not all windows versions load the dll from c:\windows\system32\wermgr.exe.local . Maybe I am missing something. 

If you know other editions in which it works, please let me know and I will edit accordingly .
