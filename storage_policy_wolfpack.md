

We have a tempoperary storage on wolfpack at `/share/ScratchGeneral/GenomicMedicine`. We request specific permissions for all files/folders in this repo (full autority for the owner and the group `g_genomic_medicine`, but no access for all other users). 
<br><br>

### Permissions

#### Check the groups you belonged to, e.g., for user zheqia
`id zheqia` 

#### change the owner of all directories 
`find /share/ScratchGeneral/GenomicMedicine -type d -exec chgrp 34760 {} \;`
#### change the owner of all files 
`find /share/ScratchGeneral/GenomicMedicine -type f -exec chgrp 34760 {} \;`

#### remove rwx permissions from all other users (i.e., members outside the group) for all directories
`find /share/ScratchGeneral/GenomicMedicine -type d -exec chmod o-rwx {} \;`
#### remove rwx permissions from all other users (i.e., members outside the group) for all files
`find /share/ScratchGeneral/GenomicMedicine -type f -exec chmod o-rwx {} \;`

#### add rwx permissions for all members in `g_genomic_medicine` for all directories 
`find /share/ScratchGeneral/GenomicMedicine -type d -exec chmod g+rwx {} \;`
#### add rwx permissions for all members in `g_genomic_medicine` for all files 
`find /share/ScratchGeneral/GenomicMedicine -type f -exec chmod g+rwx {} \;`

#### Make sure the owner have full permissions for all directories
`find /share/ScratchGeneral/GenomicMedicine -type d -exec chmod o+rwx {} \;`
#### Make sure the owner have full permissions for all directories
`find /share/ScratchGeneral/GenomicMedicine -type f -exec chmod o+rwx {} \;`

#### Print all directories created by the owner (e.g., zheqia) if the group id is not g_genomic_medicine
`find /share/ScratchGeneral/GenomicMedicine -type d -user zheqia -not -group g_genomic_medicine -print`
#### Print all directories created by zheqia if the permission is not `drwxrwx---` (numeric mode, 770)
`find /share/ScratchGeneral/GenomicMedicine -type d -user zheqia -not -perm 770 -print`

#### Print all files created by zheqia if the group id is not g_genomic_medicine
`find /share/ScratchGeneral/GenomicMedicine -type f -user zheqia -not -group g_genomic_medicine -print`
#### Print all files created by zheqia if the permission is not `-rwxrwx---` (numeric mode, 770)
`find /share/ScratchGeneral/GenomicMedicine -type f -user zheqia -not -perm 770 -print`
<br><br>


### Avoid files being deleted
Files on ScratchGeneral that have not been used for more than 6 months will be automatically deleted. Like most other HPC centres, Garvan will enable file system “flushing” for ScratchGeneral -  a technique in which old files (files that haven’t been recently accessed) will be automatically deleted (starting from the oldest). It is important to monitor the time stamps of your files to avoid them being deleted. 

#### To print old files (defined by atime)
`find /share/ScratchGeneral/GenomicMedicine -type f -atime +60 -print`
#### To touch (change the last time that they have been read) these files:
`find /share/ScratchGeneral/GenomicMedicine -type f -atime +60 -exec touch {} +`
