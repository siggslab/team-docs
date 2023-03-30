

### Accounting at NCI 

#### Computing resources

**nci_account**
You can see the current allocation and the usage so far in the quarter for any computing project you are a member of. If the project has a /g/data quota it will also report how much of this disk space is utilised. Using the -v option, you can see the usage per user:

```
nci_account -v
```

**nqstat**
`qstat` allows you to monitor your jobs at NCI. 
`nqstat` allows you to see the jobs currently submitted:

* for a given project
* for a given queue and project
* for a given user and project

Customized scripts required to check job efficiency (cpu%), the queueing time, the walltime, the cost in SU etc.

#### Storage resources

**lquota**
This command will list the quota and usage for all the projects you are a member of on both `/scratch` and `/g/data`. It will give usage and quota for both space and number of files.

**nci-files-report**
This command will list the usage in both space and number of files along different dimensions depending on options.

**Usage owned by a project per user**
If you want to know who owns files in your project or where those files are, you should use:
`nci-files-report --group tn36 --filesystem gdata`
This is probably the most useful options for the project's managers to find who has the most data owned by a project.

**Usage in a project directory per user**
If you want to know who owns files in the main directory of one of your projects, you should use:
`nci-files-report --project tn36 --filesystem gdata`

**Usage per user**
If you want to know your data footprint across all your projects in a filesystem, you should use:

`nci-files-report --user --filesystem gdata`

#### 
