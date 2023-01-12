# Storage policy on Garvan's Wolfpack
***
We have a temporary storage repo on Wolfpack located at `/share/ScratchGeneral/GenomicMedicine`. We're requesting specific permissions for all files and folders in this repo, including full authority for the owner and the group `g_genomic_medicine`, but no access for any other users.
<br><br>

### Permissions

#### Verify Your Group Memberships (e.g. for User zheqia)
`id zheqia` 

##### Modify the ownership of all directories
`find /share/ScratchGeneral/GenomicMedicine -type d -exec chgrp 34760 {} \;`
##### Modify the ownership of all files
`find /share/ScratchGeneral/GenomicMedicine -type f -exec chgrp 34760 {} \;`

##### Revoke Read, Write, and Execute Permissions for All Other Users (i.e. members outside the group) on All Directories
`find /share/ScratchGeneral/GenomicMedicine -type d -exec chmod o-rwx {} \;`
##### Revoke Read, Write, and Execute Permissions for All Other Users (i.e. members outside the group) on All Files
`find /share/ScratchGeneral/GenomicMedicine -type f -exec chmod o-rwx {} \;`

##### Grant Read, Write, and Execute Permissions for all members of the g_genomic_medicine group on All Directories
`find /share/ScratchGeneral/GenomicMedicine -type d -exec chmod g+rwx {} \;`
##### Grant Read, Write, and Execute Permissions for all members of the g_genomic_medicine group on All Files
`find /share/ScratchGeneral/GenomicMedicine -type f -exec chmod g+rwx {} \;`

##### Ensure Full Permissions for the Owner on All Directories
`find /share/ScratchGeneral/GenomicMedicine -type d -exec chmod u+rwx {} \;`
##### Ensure Full Permissions for the Owner on All Files
`find /share/ScratchGeneral/GenomicMedicine -type f -exec chmod u+rwx {} \;`

#### Verify the Success of Modifying Permissions on All Files and Folders

##### List all Directories created by the Owner (e.g. zheqia) that are not associated with the group `g_genomic_medicine`
`find /share/ScratchGeneral/GenomicMedicine -type d -user zheqia -not -group g_genomic_medicine -print`
##### List all Directories created by user (e.g., zheqia) that do not have the permissions 'drwxrwx---' (numeric mode 770) 
`find /share/ScratchGeneral/GenomicMedicine -type d -user zheqia -not -perm 770 -print`

##### List all Files created by the Owner (e.g. zheqia) that are not associated with the group `g_genomic_medicine`
`find /share/ScratchGeneral/GenomicMedicine -type f -user zheqia -not -group g_genomic_medicine -print`
##### List all Files created by user (e.g., zheqia) that do not have the permissions 'drwxrwx---' (numeric mode 770) 
`find /share/ScratchGeneral/GenomicMedicine -type f -user zheqia -not -perm 770 -print`
<br><br>


### Avoid Deletion of your Files
Like other high-performance computing centers, Garvan uses a process called 'flushing' to remove older files that have not been recently used. To be more specific, files stored in the `/ScratchGeneral` directory that have not been accessed in over six months will be automatically removed. It's important to keep track of the timestamps on your files to make sure they aren't accidentally deleted.
<br>

##### Listing of outdated files (based on Access time)
`find /share/ScratchGeneral/GenomicMedicine -type f -atime +60 -print`
##### Updating the Last-Access Time for the following Files
`find /share/ScratchGeneral/GenomicMedicine -type f -atime +60 -exec touch {} +`
 
