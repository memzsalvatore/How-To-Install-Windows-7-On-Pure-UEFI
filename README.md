# How-To-Install-Windows-7-On-Pure-UEFI
A Simple Detailed Guide On How to Install Windows 7 on Pure UEFI
                
# Warning:
Im not responsible for any damages done to your device follow the steps at your own risks. 
There May be Errors For More Info Take a look a the Notice Tab.

Updates will be Listed here: 1/18/2026

# Notice:
Windows boot Manager can Error out if not done Correctly So I Recommend backing up Your Current Linux/Windows Installation at some point


If You have multiple storage devices You Might Find the Proccess Easier If you have 2 Hdds i Recommend Force Installing it to the Location ofYour Liking Using WinNTsetup Because Windows Installers Tend to be Flaky as Hell.

You Could also Use an EFI partition on a Different drive then Installing Windows To the Partition on another drive you wanna Install It on

Also I tend To have Grammar Mistakes apologies. Im a very Lazy man

Windows 7 is good and all but I wouldn't use it as a daily machine but If you like 7 then You could use an anti virus or have common sense.

Please Note that there Might be Errors if theres any will update the guide as fast as possible

Using Adminstrator Account on Windows is VERY Dangerous therefore i mention saying this: net user administrator /active:no
The Main Reason is Because its too Risky to have Adminstrator Account active 24/7 as it has Elevated Permessions    

This Guide is For Users who have atleast have a decent amount experience to continue I dont recommend doing this as a complete Beginner

The ENTIRE thing is Made in Notepad.

If You Did Install Windows 7 If you want to web browse i Recommend theese Browsers

R3dFox: https://github.com/Eclipse-Community/r3dfox/releases/tag/v146.0

Supermium: https://github.com/win32ss/supermium/releases/tag/v138-r8

FireFox ESR(if you lost your mind): https://ftp.mozilla.org/pub/firefox/releases/115.19.0esr/win64/en-US/

Mypal (if you lost your mind): https://www.mypal-browser.org/

Make Sure to Install all Visual and Redist Drivers

Lastly If Your Device is Slow as Hell and You Dont like Linux Somehow sure Use Windows 7 (if you have UEFI to follow this guide atleast)

Also Activation Servers are Long Gone so If you havent Already you Can Try and activate it on Your own or do System maintance such As typing

Open cmd as admin type slmgr -rearm every 1 week as Windows 7 is Very aggressive and hostile if u havent activated windows for long

Or You could Find any activation metheods Online.

Lastly this Guide may not Work For you as i have tested this on an HP Prodesk 600 G2 MT Theres Alot of Different PCs/Laptops Out there that i dont exactlyKnow how to do it on so you might look into other guides

# Requirements (Necassary):

Human Requirements Aswell as:

Patience. Lots of it.

Sanity (insanity works too)

Windows PE environment of some kind 

Have a UEFI Machine

Download an iso of some kind that dosemt fail halfway. (must be x64 and between ultimate professional or enterprise.) (you also might need to slipstream it with usb 3.0 and nvme drivers.)

Download uefiseven (if you have issues with uefiseven then bad luck i dont know how to do it myself without uefiseven)
file: https://github.com/manatails/uefiseven

Download your devices drivers for windows 7 if you cant find any u can try downloading the windows 10 driver and installing it manually in 7 (may not work)

USB thumb drive at a minimum of 8 gigabytes (required)

Download Rufus: https://rufus.ie/en/ (may be required)

Download winNTsetup (optional) https://www.majorgeeks.com/files/details/winntsetup_64_bit.html

Download Winrar: https://www.win-rar.com/start.html?&L=0

Download 7zip: https://www.7-zip.org/

# Editing files and installing uefi seven (and windows 7 itself)

Open rufus and select Your USB drive and select UEFI GPT and Standard Windows installation 

Put the iso You have or just downloaded and start the flashing process (may take a while)

After flashing the iso to the usb open the usb drive and go to (UsbDrive)\EFI\Boot\

Rename bootx64.efi to bootx64.original.efi 

Unpack bootx64.efi from UefiSeven archive and copy it to (UsbDrive)\EFI\Boot\

Simply Before You Reboot You open Disk manager by Pressing Win+X or W+R type diskmgmt.msc you could Also use Diskpart if you like to but dont overcomplicate it

Partition Your Drive to the storage of your liking in Megabytes. (MBs)

After its done Reboot the computer and spam the Boot Menu Key (for most people it could be ESC F12 F9 search the motherboard boot menu key)

Select the Thumb Drive and boot.

Once booted Walk through the steps

Then Select The Partition You Just Made.

Wait For it Install (this may Take a while.)

After It's done Power off computer 

Reboot to Your windows installation or live environment 

If your windows install is intact log in as Adminstrator by Opening CMD as admin then type this: net user administrator /active:yes

Log into Adminstrator User

Open CMD again and type the following

DISKPART

LIST DISK

SELECT DISK (your windows install disk) for example DISK 0 or 1

LIST PART

SELECT PART (your efi partition its most likely formatted as fat32)

assign letter=Z

exit

exit

Now that You done This Simply open File explorer go to the EFI partition and go to (HDD)\EFI\Microsoft\Boot\

Rename bootmgfw.efi to bootmgfw.original.efi

Then take the bootx64.efi from uefiseven folder and rename it to bootmgfw.efi

Put it on (HDD)\EFI\Microsoft\Boot\

Log out of Adminstrator account and go to CMD as admimn in your user account then type: net user administrator /active:no

Reboot the computer and windows 7 should appear.

Note: if Youre on an hp computer (or any pc that supports booting via file) Boot via file and select bootmgfw.efi if it dosent Appear

# Alternative way:

Instead of Doing the above you can do this:


Extract the winNTsetup application to anywhere on Your Desktop using 7zip or winrar

Extract the windows 7 iso you just downloaded to any locaction on the drive

Launch winNTsetup

Select the EFI partition

Select the Partition You are going to Install windows 7 On

Select the Installation Files and navigate to the isos directory go to sources and select install.wim or install.esd 

Make it update The BootCode and find other versions of windows if youre dualbooting.

Wait for It to finish (may take a while)

After its done dont Reboot 

Log in As Adminstrator by opening command prompt as admin and type this: net user administrator /active:yes

Log in to Adminstrator and go to the efi partition if you cant see it on file explorer do this

Open CMD as admin and type the following

DISKPART

LIST DISK

SELECT DISK (your windows install disk) for example DISK 0 or 1

LIST PART

SELECT PART (your efi partition its most likely formatted as fat32)

assign letter=M

exit

exit


Now Go to (HDD)\EFI\Microsoft\Boot\

Rename bootmgfw.efi to bootmgfw.original.efi
 
Then take the bootx64.efi from uefiseven folder and rename it to bootmgfw.efi

Put it on (HDD)\EFI\Microsoft\Boot\

Log out of Adminstrator account and go to CMD then type: net user administrator /active:no

Reboot the computer and windows 7 should appear.

Note: if Youre on an hp computer (or any pc that supports booting via file) Boot via file and select bootmgfw.efi if it dosent Appear

