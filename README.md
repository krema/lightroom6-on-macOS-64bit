# lightroom6-backup-restore-to-catalina
Instructions for backing up and restoring the Adobe Lightroom6 program on MacOS Catalina without using the 32-bit installer.

## Why?
When I upgraded to MacOS Catalina, my Mac did not work as expected, so I needed a clean reinstall without using the migration wizard from Timemachine Backup. Also I could not use the installer because of the 32-bit problem.
Then I checked what files the installer has installed and documented how I backed up and restored Lightroom on the new Mac installation without the need of the installer.

## Prerequisites

 - Installed & activated Lightroom 6 
 - The restored copy works only on the same computer where it was previously installed.
 - **Important:** Replace <YOUR_USER> in lightroom6.txt and before executing the rsync commands

## Instructions
 
All you need to do is executing the following in the Terminal.app.

**If you decide to run it, you do so on your own risk! I assume no liability for the accuracy, correctness, completeness, or usefulness of any information provided by this repository nor for any sort of damages using these scripts may cause.**

### Backup

    rsync -avm --include-from=/Users/<YOUR_USER>/Downloads/lightroom6.txt / /Users/<YOUR_USER>/Downloads/Lightroom6_Backup
     
 Copy the Lightroom6_Backup folder to an external drive. Now you can reinstall Mac OS.
 

### Restore

    sudo rsync -avm /Users/<YOUR_USER>/Downloads/Lightroom6_Backup/* /
