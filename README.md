# Active Directory Auditing Content Pack Dashboards *Beats Edition*

Tested with nxLog/Windows 2012R2 Domain Controllers/Graylog 3.0.2/WinLogBeats

This content pack provides several useful dashboards for auditing Active Directory events:
* DNS Object Summary - DNS Creations, Deletions
* Group Object Summary - Group Creations, Modifications, Deletions, Membership Changes
* User Object Summary - Account Creations, Deletions, Modifications, Lockouts, Unlocks
* Computer Object Summary - (in progress)
* Logon Summary - Failed Authentication Attempts, Interactive Logins

## Includes

* Dashboards 

## Requirements

* WinLogBeats collecting windows logs from all domain controllers, other log collectors will work but may require modifying the searches to match the different fields outputted by other collectors
* Domain Controller secuirty policy with the following enabled:
** Audit Account Logon Events
** Audit Account Managmenet
** Audit Logon Events
** Audit Object Access
** Audit Policy Change
** Audit System Events
* Leading Wildcard Searches enabled in graylog.conf:  allow_leading_wildcard_searches = true

## Screenshots

![Dashboard](http://www.ohjeah.net/wp-content/uploads/2015/09/ad_audit.png)

##  NXLOG vs WinLog Beats

It is possible to use this with NXLOG but you would need to convert the NXLOG event fields to the Beats equivalents.

For example EventID (NXLOG) vs event_id (WinLogBeats)

For other event fields they are prefixed with event_data_(Name), such as event_data_TargetUserName, so you would need to adjust all event field names to match Beats.  