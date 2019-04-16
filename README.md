# HetznerRuncloudJoomlaScripts
These scripts are specifically designed to use on Runcloud powered servers running at Hetzner.

---

These scripts can do the following:

* **jfunctions**<br/>The jfunctions script retrieves general information about a Joomla website like Joomla version, sitename, database credentials etc. This script is used by most other scripts.
* **joomlainfo**<br/>The joomlainfo script display general information about a Joomla website.
* **jlistjoomlas**<br/>The jlistjoomlas script searches and lists all Joomla websites found on your Runcloud server.
* **jdbdump**<br/>The jdbdump script creates a database dump of a Joomla website.
* **jdbdumpall**<br/>The jdbdumpall script creates database dumps of all Joomla websites found on a Runcloud server. All database dumps are stored in a separated map on the server, default at /backups/mysql. Each database dump has a unique date/time stamp. Database dumps older than x days are automatically deleted.
* **jdbimp**<br/>The jdbimp script imports a database dump into the database of a Joomla website.
* **jakeebabackup** The jakeebabackup script creates a Joomla website backup by executing the Akeeba Backup CLI script. Obviously Akeeba Backup needs to be installed on your Joomla website.
* **jakeebabackupall**<br/>The jakeebabackupall script creates backups of all Joomla websites on your Runcloud server by executing the Akeeba Backup CLI script for each website found. Obviously Akeeba Backup needs to be installed on these Joomla websites. All backups are stored in a separated map on the server, default at /backups/sites. Each backup has a unique date/time stamp. Backups older than x days are automatically deleted.
* **jsitesbackup**<br/>The jsitesbackup script creates backups of all Joomla websites on your Runcloud server by trying to execute the Akeeba Backup CLI script for each website found. Obviously Akeeba Backup needs to be installed on these Joomla websites. If the script can't find Akeeba Backup it tries to create a tar-gzip or zip backup. All backups are stored in a separated map on the server, default at /backups/sites. Each backup has a unique date/time stamp. Backups older than x days are automatically deleted.
* **jremotesitesbackup**<br/>The jremotesitesbackup script creates backups of all Joomla websites on your Runcloud server by trying to execute the Akeeba Backup CLI script for each website found. Obviously Akeeba Backup needs to be installed on these Joomla websites. If the script can't find Akeeba Backup it tries to create a tar-gzip or zip backup. All backups are stored in a separated map on the server, default at /backups/jpatmp. These backups have no date/time stamp. This script was specifically designed to use in combination with the jtransferbackups script.
* **jtransferbackups**<br/>The jtransferbackups script transfers backups found at /backups/jpatmp to a remote Hetzner storage box. Optionally the local backup files are deleted after transfer.

## Installation instructions
1. Copy all scripts to the map /usr/local/sbin on your Runcloud server.

2. Make each script executable by doing chmod +x for each script:
```
chmod +x /usr/local/sbin/jakeebabackup
chmod +x /usr/local/sbin/jakeebabackupall
chmod +x /usr/local/sbin/jdbdump
chmod +x /usr/local/sbin/jdbdumpall
chmod +x /usr/local/sbin/jdbimp
chmod +x /usr/local/sbin/jfunctions
chmod +x /usr/local/sbin/jlistjoomlas
chmod +x /usr/local/sbin/joomlainfo
chmod +x /usr/local/sbin/jremotesitesbackup
chmod +x /usr/local/sbin/jsitesbackup
chmod +x /usr/local/sbin/jtransferbackups
```


3. Create folders for the storage of backups:
```
mkdir -p /backups/mysql; mkdir -p /backups/sites; mkdir -p /backups/jpatmp
```

4. Create cronjobs to run regular backups:
```
# create a backup every night at 1:30 for all Joomla websites
30 1 * * * /usr/local/sbin/jsitesbackup -s
# create a database dump every 6 hours for all Joomla websites
20 */6 * * * /usr/local/sbin/jdbdumpall -s
```
