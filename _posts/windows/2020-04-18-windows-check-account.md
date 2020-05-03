---
layout: post
title:  "How to check if AD account is locked"
date:   2020-04-18 09:10:55 -0400
img: powershell.png
categories: Windows
tags: Shell
---
![PowerSheel]({{site.baseurl}}/images/powershell.png)

### Check if AD account is locked
If LockedOut is True, the account is locked
{% highlight ruby %}

PS C:\Users\trevorl> Get-ADUser trevorl -Properties LockedOut

DistinguishedName : CN=pxos_lxha_fencing,OU=Corporate,OU=NonPeople Objects,OU=Enterprise Privileged
                    Objects,DC=TDBFG,DC=com
Enabled           : True
GivenName         : trevorl
LockedOut         : True
Name              : pxos_lxha_fencing
ObjectClass       : user
ObjectGUID        : b36dc918-59e9-437f-81af-802a60e4ae7e
SamAccountName    : trevorl
SID               : S-1-5-21-3088935761-3292726799-943891260-897930
Surname           :
UserPrincipalName : trevorl@EXAMPLE.COM
{% endhighlight %}
