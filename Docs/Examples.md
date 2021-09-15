### Get-NTFSAccess
Returns a list of all access control entries found on the given object(s).

    #Get permissions from all files or folders in the current folder
    dir | Get-NTFSAccess

    #to read the permissions of a specific file
    Get-NTFSAccess -Path C:\Windows

#### Get permissions from all files or folders in the current folder

    dir | Get-NTFSAccess

#### To read and also remove only the explicitly assigned ones

    dir | Get-NTFSAccess -ExcludeInherited | Remove-NTFSAccess

The pipeline support can also be used to backup and restore permissions of one or many items:
PowerShell

#### To backup permissions just pipe what Get-NTFSAccess returns to Export-Csv

    dir | Get-NTFSAccess -ExcludeInherited | Export-Csv permissions.csv

#### To retore the permissions pipe the imported data to Get-NTFSAccess

As the imported data also contains the path you do not need to specify the item

    Import-Csv .\permissions.csv | Get-NTFSAccess

All cmdlets can handle SIDs and also SamAccountNames. The output always contains both unless a SID is not resolvable.
The types.ps1xml file is extending the common objects with some useful information. The format.ps1xml file formats all the output in the same way as the Get-ChildItem output.

By implementing the [Process Privilege http://processprivileges.codeplex.com/] project, the cmdlets can activate the required privileges for setting the ownership.


# Add-NTFSAccess

Adds a specific account to the current object: 

     Get-Item .\VMWare | Add-NTFSAccess -Account Contoso\JohnD -AccessRights FullControl

# Get-NTFSAccess

Gets a list of all permissions for a given directory:

    Get-Item F:\backup | Get-NTFSAccess

Gets a list of all non-inherited permissions for a given directory:

    Get-Item F:\backup | Get-NTFSAccess –ExcludeInherited


## Filtering works with Where-Object

    Get-Item F:\backup | Get-NTFSAccess | Where-Object { $_.ID -like "*users*" }

# Get-NTFS Orphaned  Access

Get a list of all permissions that can no longer be resolved. If the account is no longer available, the permissions will show up as SIDs rather than account names.

    Get-Item F:\backup -Recurse | Get-NTFSOrphanedAccess

To remove all non-resolvable or orphaned permissions you can use the following line. But be very careful with that as maybe the account is not resolvable due to a network problem.

    Get-Item F:\backup -Recurse | Get-NTFSOrphanedAccess | Remove-NTFSAccess

# Remove- NTFSAccess

Removes the permission for a certain account. As the pipeline is supported it takes also ACEs coming from Get-NTFSAccess or Get-NTFSOrphanedAccess


# Get-NTFSEffectiveAccess

Shows the permissions an account actually has on a file or folder. If no parameter is specified it shows the effective permissions for the current user. However you can supply a user by using the SID or account name
PowerShell

    Get-Item F:\backup | Get-NTFSEffectiveAccess -Account S-1-5-32-545

# Get-NTFSInheritance
Shows if inheritance is blocked

# Enable-NTFSInheritance
It can be a problem if certain files or folders on a volume have inheritance disabled. Making sure that inheritance is enabled can be done using this cmdlets:

    Get-Item .\Data -Recurse | Enable-NTFSAccessInheritance

# Disable-NTFSInheritance
See Enable-NTFSInheritance
    Get-Item .\Data -Recurse | Disable-NTFSAccessInheritance

# Get-NTFSOwner
Shows the owner of a file or folder

    Get-Item .\Data -Recurse | Get-NTFSOwner

# Set-NTFSOwner
Sets the owner to a specific account like:

    Get-Item .\Data | Set-NTFSOwner -Account builtin\administrators
