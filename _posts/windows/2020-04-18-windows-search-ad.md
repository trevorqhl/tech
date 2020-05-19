---
layout: post
title:  "How to search Active Directory"
date:   2020-04-18 09:10:55 -0400
img: powershell.png
categories: Windows
tags: Active_Directory
---
![PowerSheel]({{site.baseurl}}/images/ad.png)

### Search AD account from Linux
{% highlight ruby %}
# Get all users
ldapsearch -xLLL  -H ldap://EXAMPLE.COM -D 'EXAMPLE\trevorl' -E pr=1000/noprompt -b 'OU=Users,OU=tdbg,DC=example,DC=com' -W

# Get a specifc user
ldapsearch -xLLL  -H ldap://EXAMPLE.COM -D 'EXAMPLE\trevorl' -E pr=1000/noprompt -b 'OU=Users,OU=tdbg,DC=example,DC=com' -W uid=trevorl

# Enter the passsword to command without prompting 
ldapsearch -xLLL  -H ldap://EXAMPLE.COM -D 'EXAMPLE\trevorl' -E pr=1000/noprompt -b 'OU=Users,OU=tdbg,DC=example,DC=com' -w 'password' uid=trevorl
{% endhighlight %}

### Search AD account from Windows
{% highlight ruby %}
Get-ADUser -LDAPFilter "(SamAccountName=trevorl)"
Get-ADUser -LDAPFilter "(SamAccountName=trevorl)" -Properties *
{% endhighlight %}

### Search computer from Linux
{% highlight ruby %}
ldapsearch -xLLL  -H ldap://EXAMPLE.COM -D 'EXAMPLE\trevorl' -E pr=1000/noprompt -b 'OU=RHEL,OU=Servers,OU=Cloud,DC=example,DC=com' -w 'password' name=webhost1
{% endhighlight %}

### Search computer by Ambiguous Name Resolution Filter from Windows Powershell
{% highlight ruby %}
Get-ADComputer -LDAPFilter "(anr=server1)"
Get-ADComputer -LDAPFilter "(anr=server2)" -Properties *

# Search for a differnt domain than what is currently login
$tempCreds = (Get-Credential)
Get-ADComputer -LDAPFilter "(anr=servername)" -Server example.com -Credential $tempCreds
{% endhighlight %}

### Check if AD account is locked from Windows
{% highlight ruby %}
# The account is locked if LockedOut is True
Get-ADUser trevorl -Properties LockedOut
{% endhighlight %}

### Check if AD account is locked from Linux
{% highlight ruby %}
# The account is not locked out if lockoutTime is zero
ldapsearch -xLLL  -H ldap://EXAMPLE.COM -D 'EXAMPLE\trevorl' -E pr=1000/noprompt -b 'OU=Users,OU=tdfg,DC=example,DC=com' -W uid=trevorl | grep -i lockoutTime
{% endhighlight %}
