---
layout: post
title:  "How to use PowerShell check computer object"
date:   2020-04-18 09:10:54 -0400
img: powershell.png
categories: Windows
tags: Shell
---
![PowerSheel]({{site.baseurl}}/images/powershell.png)

### AD PowerShell module on Windows 10
{% highlight ruby %}
Import-Module ActiveDirectory
Get-ADForest
Get-ADDomain -Server tdbfg.com
Get-ADDomainController -Server tdbfg.com

Get-ADUser -LDAPFilter "(SamAccountName=trevorl)"
Get-ADUser -LDAPFilter "(SamAccountName=trevorl)" -Properties mail, memberOf
Get-ADUser -LDAPFilter "(SamAccountName=trevorl)" -Properties *

### Example of a global catalogue (GC) connection using port 3268:
Get-ADUser -LDAPFilter "(anr=test)" -Server example.com:3268

### Example of a connection to a specific domain
Get-ADUser -LDAPFilter "(anr=test)" -Server example.com

### Example of a connection to a trusted domain (i.e., abc, MMI)
Get-ADUser -LDAPFilter "(anr=test)" -Server example.com


### Example of retrieving a computer object
Get-ADComputer -LDAPFilter "(anr=server1)"
Get-ADComputer -LDAPFilter "(anr=server2)" -Properties *

### Example of connecting to a lower environment from prod
### Enter your credentials in the format of domain\id, etc.
$tempCreds = (Get-Credential)
Get-ADComputer -LDAPFilter "(anr=servername)" -Server example.com -Credential $tempCreds
{% endhighlight %}
