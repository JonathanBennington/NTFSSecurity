---
external help file: NTFSSecurity.dll-Help.xml
Module Name: ntfssecurity
online version:
schema: 2.0.0
---

# Get-NTFSEffectiveAccess

## SYNOPSIS

{{ Fill in the Synopsis }}

## SYNTAX

### Path (Default)
```
Get-NTFSEffectiveAccess [[-Path] <String[]>] [[-Account] <IdentityReference2>] [-ServerName <String>]
 [-ExcludeNoneAccessEntries] [<CommonParameters>]
```

### SecurityDescriptor
```
Get-NTFSEffectiveAccess [-SecurityDescriptor] <FileSystemSecurity2[]> [[-Account] <IdentityReference2>]
 [-ServerName <String>] [-ExcludeNoneAccessEntries] [<CommonParameters>]
```

## DESCRIPTION

{{ Fill in the Description }}

## EXAMPLES

### Example 1

```PowerShell
PS C:\> {{ Add example code here }}
```

{{ Add example description here }}

## PARAMETERS

### -Account

{{ Fill Account Description }}

```yaml
Type: IdentityReference2
Parameter Sets: (All)
Aliases: NTAccount, IdentityReference

Required: False
Position: 2
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -ExcludeNoneAccessEntries

{{ Fill ExcludeNoneAccessEntries Description }}

```yaml
Type: SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Path

{{ Fill Path Description }}

```yaml
Type: String[]
Parameter Sets: Path
Aliases: FullName

Required: False
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -SecurityDescriptor

{{ Fill SecurityDescriptor Description }}

```yaml
Type: FileSystemSecurity2[]
Parameter Sets: SecurityDescriptor
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -ServerName

{{ Fill ServerName Description }}

```yaml
Type: String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters
This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable. For more information, see [about_CommonParameters](http://go.microsoft.com/fwlink/?LinkID=113216).

## INPUTS

### System.String[]

### Security2.FileSystemSecurity2[]

### Security2.IdentityReference2

## OUTPUTS

### Security2.FileSystemAccessRule2

## NOTES

## RELATED LINKS