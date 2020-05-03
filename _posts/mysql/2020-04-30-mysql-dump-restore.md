---
layout: post
title:  "How to backup and restore MySQL"
date:   2020-04-30 09:30:52 -0400
img: mysql.png
categories: MySQL
tags: Database
---

![Linux]({{site.baseurl}}/images/mysql.png)

### Use mysqldump to backup
```
mysqldump --host=db_host --user=db_user --password=db_password --compress --add-drop-table \
--extended-insert --quote-names db_name > mysql.dump
```
### Restore from dump
```
mysql --host=db_host --user=db_user --password=db_password db_name < mysql.dump

```
