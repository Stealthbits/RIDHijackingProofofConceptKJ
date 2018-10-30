# RID Hijacking Proof of Concept
RID Hijacking Proof of Concept script by Kevin Joyce

## Description
The concept of RID Hijacking is a persistence technique that can be leveraged by attackers to gain a foothold on a compromised Windows system. RID Hijacking takes the RID(500) of the Administrator account, and puts it on the Guest account. This is done by modifying the registry with SYSTEM level access. Once the Guest account has the new RID, it has Administrator level access.

RID Hijacking Script- runs PowerShell as SYSTEM and modifies a registry value associated with the Guest account. Sets the RID to 500 (Administrator), enables, and sets the password for the Guest account. Once complete, it will pause and allow the user to test the new RID of the Guest account, and upon continuing, will revert all changes. The objective of this script is to be a proof of concept for a RID Hijacking persistence technique. This technique allows an attacker to use the Guest account with administrative privileges.

## Usage
1. Install PSExec - https://docs.microsoft.com/en-us/sysinternals/downloads/psexec
2. Open a command prompt as administrator and navigate to the location of PSExec
3. Modify the [pathToScript] block below to include the path to the RIDHIJACK.ps1 script
4. Run the following command: .\Psexec.exe -accepteula -s -i powershell.exe [pathToScript]\RIDHIJACK.ps1
5. When prompted, open a command prompt as Guest (shift+right click Run as a different user), follow instructions on the command prompt window.
6. In the command prompt window run "whoami /all" to see that the RID of the Guest account has been changed to 500 and that it has all assoicated privileges from the Administrator account.
7. Continue with the script to revert all changes.
