# Synology NAS Shared Folder as Home Assistant Backup
This guide is to set up a **Synology NAS** to store backups from my Home Assistant setup. Instead of keeping backups on the local storage, I wanted a more reliable and automated way to store them on my NAS. Here's how I got it working.


## Step 1: Access and Create a Shared Folder on Synology NAS
1. Log in to your **Synology NAS**.  
2. Open **Control Panel** → **Shared Folder** → **Create**.  
3. Name the folder (e.g., `ha-backups`).  
4. In the NFS Permission tab, Capture the HA IP address in the Host IP and update previlege and other security settings. Save the chagnes. 
4. Note down the Mount path display at the bottom of the page. Refer screenshot for details. 
   
![Synalogy NAS Shared Path](/images/shared-backup-synology.png)

## Step 2: Mount the NAS Shared Folder on Home Assistant  

1. Go to Settings > System > Storage in the UI. Select Add network storage.
2. Fill out all the information for your network storage as handled in the Step 1

![Home Assistant Setup](/images/shared-backup-homeassistant.png)

## Step 3: Update Backup location to the new location. 
1. If you are using [Google Drive Backup for HA](https://github.com/sabeechen/hassio-google-drive-backup), go to Settings, Update the Home Assistant Backup location with the newly created Synology Shared folder backup location. 

![Google Drive Backup](/images/shared-backup-googledrive.png)

Happy backuping :-)