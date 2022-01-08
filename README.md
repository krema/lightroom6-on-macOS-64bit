
# lightroom6-backup-restore-to-catalina-bigsur
Instructions for backing up and restoring the Adobe Lightroom6 program on **MacOS Catalina**, **Big Sur** & **Monterey** on **Intel** and **Apple M1** machines without using the 32-bit installer.

## Why?
Adobe will not update its installers, so we will not be able to install Adobe Lightroom 6 on newer 64-bit-only MacOS versions. The [support website](https://helpx.adobe.com/lightroom-cc/kb/macos-catalina-compatibility.html) says:
 

> Older versions use 32-bit licensing components and installers. Therefore, they cannot be installed and activated after upgrading to macOS Catalina. Although upgrading to macOS Catalina with an older version already installed on your computer may allow the app to function in some capacity, you will not be able to reinstall or activate the app after the macOS upgrade.

## Known Issues

 - The import and playback of videos is no longer possible.
 - The app freezes from time to time on exit (no need to worry)
 - It seems Rosetta 2 loses the activation after restarting the program

## Prerequisites

 - Installed & activated Lightroom 6 on MacOS before Catalina
 - Download the *lightroom6.txt* file from this repository to your machine with Lightroom 6 installed
 - **Important:** Replace <YOUR_USER> in *lightroom6.txt* and before executing the rsync commands

## Instructions
 
All you need to do is executing the following in the Terminal.app.

**If you decide to run it, you do so on your own risk! I assume no liability for the accuracy, correctness, completeness, or usefulness of any information provided by this repository nor for any sort of damages using these scripts may cause.**

### Backup

    rsync -avm --include-from=/Users/<YOUR_USER>/Downloads/lightroom6.txt / /Users/<YOUR_USER>/Downloads/Lightroom6_Backup
     
 Copy the Lightroom6_Backup folder to an external drive. Now you can reinstall Mac OS.
 

### Restore

    sudo rsync -avm /Users/<YOUR_USER>/Downloads/Lightroom6_Backup/* /
    
#### Disable EULA

Now comes the interesting part. We accept the EULA manually in code. 


    vim /Library/Application\ Support/Adobe/Adobe\ Lightroom\ AMT/AMT/application.xml 

    Add a new Data tag
    
        <Data key="EULADelay">-1</Data>
    
    inside your existing payload 
    
        <Payload adobeCode="{XYZXYZXYZXYZXYZXYZ}"></Payload>
