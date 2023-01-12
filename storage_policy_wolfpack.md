# Storage policy on Garvan's Wolfpack

We have a temporary storage repo on Wolfpack located at `/share/ScratchGeneral/GenomicMedicine`. We want to ensure that the proper access rights are set for all files and directories in this repository, giving the owner and group g_genomic_medicine complete control, while limiting all other users to read-only access.
<br><br>

### Permissions

#### Verify Your Group Memberships (e.g. for User zheqia)
`id zheqia` 

```
GML=/share/ScratchGeneral/GenomicMedicine
cd GML
```

##### Modify the ownership of all directories
`find . -type d -exec chgrp 34760 {} \;`
##### Modify the ownership of all files
`find . -type f -exec chgrp 34760 {} \;`

##### Revoke Write and Execute Permissions for All Other Users (i.e. members outside the group) on All Directories
`find . -type d -exec chmod o-rwx {} \;`
`find . -type d -exec chmod o-rwx {} \;`
##### Revoke Read Write, and Execute Permissions for All Other Users (i.e. members outside the group) on All Files
`find . -type f -exec chmod o+r {} \;`
`find . -type d -exec chmod o+r {} \;`

##### Grant Read, Write, and Execute Permissions for all members of the g_genomic_medicine group on All Directories
`find . -type d -exec chmod g+rwx {} \;`
##### Grant Read, Write, and Execute Permissions for all members of the g_genomic_medicine group on All Files
`find . -type f -exec chmod g+rwx {} \;`

##### Ensure Full Permissions for the Owner on All Directories
`find . -type d -exec chmod u+rwx {} \;`
##### Ensure Full Permissions for the Owner on All Files
`find . -type f -exec chmod u+rwx {} \;`

#### Verify the Success of Modifying Permissions on All Files and Folders

##### List all Directories created by the Owner (e.g. zheqia) that are not associated with the group `g_genomic_medicine`
`find . -type d -user zheqia -not -group g_genomic_medicine -print`
##### List all Directories created by user (e.g., zheqia) that do not have the permissions 'drwxrwxr--' (numeric mode 775) 
`find . -type d -user zheqia -not -perm 775 -print`

##### List all Files created by the Owner (e.g. zheqia) that are not associated with the group `g_genomic_medicine`
`find . -type f -user zheqia -not -group g_genomic_medicine -print`
##### List all Files created by user (e.g., zheqia) that do not have the permissions '-rwxrwxr--' (numeric mode 775) 
`find . -type f -user zheqia -not -perm 775 -print`
<br><br>


### Avoid Deletion of your Files
Like other high-performance computing centers, Garvan uses a process called 'flushing' to remove older files that have not been recently used. To be more specific, files stored in the `/ScratchGeneral` directory that have not been accessed in over six months will be automatically removed. It's important to keep track of the timestamps on your files to make sure they aren't accidentally deleted.
<br>

##### Listing of outdated files (based on Access time)
`find . -type f -atime +60 -print`
##### Updating the Last-Access Time for the following Files
`find . -type f -atime +60 -exec touch {} +`
 
