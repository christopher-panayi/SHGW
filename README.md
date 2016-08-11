### Simple Hash Generator for Windows - A bat file and some reg files that wrap the built in -hashfile functionality in certutil.

These scripts will create an extra context menu option when right clicking on any file in Windows Explorer that will generate various hashes for that file. Main reason this exists is because I was tired of hashing files manually in command prompt in Windows and wanted to find an easy way to leverage the built in functionality provided by Microsoft. Main use case for me is checking file integrity against known good hashes before installing software or using a downloaded ISO.

This script should work in any version of Windows where certutil supports the -hashfile argument.

## Installation

 * Place "Hash Generator" Folder into "C:\Program Files\"
 * Run GenerateHashOption.reg

## Usage

 * Right click on file to hash -> Hover over "Generate Hash" Menu Option -> Pick hash type -> Profit :)
 
## Removal
 
 * "Uninstalling" simply requires running RemoveGenerateHashOption.reg and deleting the associated files from disk (i.e. the "C:\Program Files\Hash Generator" folder)
 
## Notes to the interested user
 
 * GenerateHashOption.reg will create the Explorer context option in the HKEY_LOCAL_MACHINE registry subtree, meaning it needs admin rights to create the relevant registry keys (...but you'd need admin rights to paste the batch file into Program Files anyway :P). Because it's in LOCAL_MACHINE, it will thus make the "Generate Hash" context option visible to all users of the machine. This isn't really an issue, but if non-admin "installation" is required, or there is a need to hide the Explorer option from other users on the machine, there should be a user specific way to create the same Explorer context options. See the MSDN resources given below for more information.
 * The path to the batch is hardcoded to C:\Program Files\Hash Generator\hash.bat, but can easily be changed by editing GenerateHashOption.reg for the various hash types provided.
 
## Resources

 * Certutil documentation - https://technet.microsoft.com/en-us/library/cc732443(v=ws.11).aspx 
 
 * Extending Shortcut Menus - https://msdn.microsoft.com/en-us/library/windows/desktop/cc144101(v=vs.85).aspx
 * Creating Shortcut Menu Handlers - https://msdn.microsoft.com/en-us/library/windows/desktop/cc144171(v=vs.85).aspx
 * Pretty picture walkthrough for adding Explorer context options - http://www.howtogeek.com/107965/how-to-add-any-application-shortcut-to-windows-explorers-context-menu/
 
 * A whole bunch of bat file stuff on Stack Overflow :)