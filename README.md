# lightroom6-backup-restore-to-catalina
Instructions for backing up and restoring the Adobe Lightroom6 program on MacOS Catalina without using the 32-bit installer.

## Why?
When I upgraded to MacOS Catalina, my Mac did not work as expected, so I needed a clean reinstall without using the migration wizard from Timemachine Backup. Also I could not use the installer because of the 32-bit problem.
Then I checked what files the installer has installed and documented how I backed up and restored Lightroom on the new Mac installation without the need of the installer.

## Prerequisites

 - Installed & activated Lightroom 6 
 - The restored copy works only on the same computer where it was previously installed.

## Instructions
 
All you need to do is executing the following in the Terminal.app:

### Backup

    rsync -avm --include-from=/Users/<YOUR_USER>/Downloads/lightroom6.txt / /Users/<YOUR_USER>/Downloads/Lightroom6_Backup 

### Restore

    sudo rsync -avm /Users/<YOUR_USER>/Downloads/Lightroom6_Backup/* /
