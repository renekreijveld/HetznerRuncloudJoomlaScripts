# HetznerRuncloudJoomlaScripts
These scripts are specifically designed to use on Runcloud powered servers running at Hetzner.

---

These scripts can do the following:

* **jfunctions** The jfunctions script retrieves general information about a Joomla website like Joomla version, sitename, database credentials etc. This script is used by most other scripts.
* **joomlainfo** The joomlainfo script display general information about a Joomla website.
* **jlistjoomlas** The jlistjoomlas script searches and lists all Joomla websites found on your Runcloud server.
* **jdbdump** The jdbdump script creates a database dump of a Joomla website.
* **jdbdumpall** The jdbdumpall script creates database dumps of all Joomla websites. All database dumps are stored in a separated map on the server, default at /backups/mysql. Each database dump has a unique date/time stamp. Database dumps older than x days are automatically deleted.
* **jdbimp** The jdbimp script imports a database dump into the database dump of a Joomla website.
* **jakeebabackup** The jakeebabackup script creates a Joomla website backup by executing the Akeeba Backup CLI script. Obviously Akeeba Backup needs to be installed on your Joomla website.
* **jakeebabackupall** The jakeebabackupall script creates backups of all Joomla websites on your Runcloud server backup by executing the Akeeba Backup CLI script. Obviously Akeeba Backup needs to be installed on these Joomla websites. All backups are stored in a separated map on the server, default at /backups/sites. Each backup has a unique date/time stamp. Backups older than x days are automatically deleted.
* **jsitesbackup** The jsitesbackup script creates backups of all Joomla websites on your Runcloud server backup by trying to execute the Akeeba Backup CLI script. Obviously Akeeba Backup needs to be installed on these Joomla websites. If the script can't find Akeeba Backup it tries to create a tar-gzip or zip backup. All backups are stored in a separated map on the server, default at /backups/sites. Each backup has a unique date/time stamp. Backups older than x days are automatically deleted.
* **jremotesitesbackup** The jremotesitesbackup script creates backups of all Joomla websites on your Runcloud server backup by trying to execute the Akeeba Backup CLI script. Obviously Akeeba Backup needs to be installed on these Joomla websites. If the script can't find Akeeba Backup it tries to create a tar-gzip or zip backup. All backups are stored in a separated map on the server, default at /backups/jpatmp. These backups have no date/time stamp. This script was specifically designed to use in combination with the transferbackups script.
* **transferbackups** The transferbackups script transfers backups found at /backups/jpatmp to a remote Hetzner storage box. Optionally the local backup files are deleted after transfer.

All of these scripts should be installed at /usr/local/sbin with the execute flag on.

Each script can be called with a -h (help) parameter to see the various options.