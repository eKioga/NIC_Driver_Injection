# NIC_Driver_Injection

Dell doesn't have a PE driver for the E7470. Here is the workaround.

PXE boot to MDT then push F8 to get a command prompt. Type in ipconfig. If you get an IP address, your done. Do not continue. 

If ipconfig comes back empty, first step is to run the driver.bat file located on the USB drive. It should generaly be located on the D,E or F drive. 

Execute the batch file by typing in one of the following:
D:\driver.bat
E:\driver.bat
F:\driver.bat

If none of this works. type in 'diskpart' then 'list volume' to see what drive letter the USB drive has, the adjust accordingly. 
THe batch file assumes that the USB drive letter will be either D, E or F. If it's neither of these, then you can redo the failed steps on the screen but useing the correct drive letter.

The driver was successfully installed if ipconfig displays an IP address. If ipconfig is empty, the script failed to install a usable driver.

MANUAL INSTRUCTIONS: incase the script sucks or your running this script on the wrong laptop.

	1. Download the network driver.
	2. Rename the .exe to .zip and find the appropriate architecture and OS version and extract it to a USB flash drive. May need 7zip.
	3. At the WinPE UNC share / accesses rights step, push F8 and do the following.
	4. Type in "diskpart" then "list volume" to see the USB drive letter. Type "exit" to leave.
	5. Type in the drvload command along with the location of the .inf file. 
		a. Example: drvload D:\Windows10-x64\E1D65x64.inf
	6. Then type in "wpeutil initializeNetwork" to reinitialize the network.
	7. Then type in "ipconfig" to see if your given an IP. 
IF so, then continue on with the MDT deployment. If not, try another driver inf file.
