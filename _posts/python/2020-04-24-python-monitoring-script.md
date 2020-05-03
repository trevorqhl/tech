---
layout: post
title:  "Create a Python script to monitor Red Hat Cluster Resource" 
date:   2020-04-24 20:30:52 -0400
img: python.png
categories: Python
tags: Programming
---

![Linux]({{site.baseurl}}/images/python.png)


* Create a json file to define the resources you want to montior
{% highlight ruby %}
{
  "haresource": [
     { "name": "fence_agent1",
       "type": "stonith",
       "sleep": 300,
       "retry": 3
     },

     { "name": "fence_agent2",
       "type": "stonith",
       "sleep": 300,
       "retry": 3
     },

     { "name": "httpd",
       "type": "resource",
       "sleep": 300,
       "retry": 3
     }
  ]
}
{% endhighlight %}

* Script to monitor the resources 
{% highlight ruby %}
#!/usr/bin/python
import sys
import os
import commands
import json
import time
import random
import getpass
from datetime import datetime

class hamonitor:

  def __init__(self, name, node, operation, state):
      # Support log level 0, 1, 2
      self.debug = 0
      self.node = node
      self.operation = operation
      self.state = state
      self.conf = "/var/lib/pacemaker/haresource.json"
      self.logfile = "/var/log/cluster/hamonitor.log"
      self.pid = os.getpid()
      self.user = getpass.getuser()
 
      self.name = "none"
      self.type = "none"
      with open(self.conf) as f:
           data = json.load(f)
           for item in data['haops']:
             if item['name'] == name:
                self.name = item['name']
                self.type = item['type']
                self.sleep = item['sleep']
                self.retry = item['retry']

      if self.name == "none":
         self.log(0, name, "Resource not matched")
         exit()
      self.log_vars()

  def __del__(self):
      self.log(0, "script.exit", str(self.pid))   

  def run(self):
      if self.check_process():
         index = 1
         while index <= self.retry:
           sleep_time =  round(random.uniform(self.sleep, self.sleep + 5), 2)
           self.log(0, "sleep", str(sleep_time))
           time.sleep(sleep_time) 
           if self.check_failcount():
              if self.cleanup():
                 break;
           else:
              break
           index += 1

  def log_vars(self):
      self.log(2, "self.pid", str(self.pid))
      self.log(2, "self.name: ", self.name)
      self.log(2, "self.node: ", self.node)
      self.log(2, "self.operation: ", self.operation)
      self.log(2, "self.state: ", self.state)
      self.log(2, "self.type: ", self.type)
      self.log(2, "self.sleep: ", str(self.sleep))
      self.log(2, "self.retry: ", str(self.retry))

  def cleanup(self):
      cmd = "pcs resource cleanup " + self.name
      if self.run_command(cmd) == 0:
         self.log(0, "cleanup", "Cleanup OK")
         return True
      else:
         self.log(0, "cleanup", "ITM Mon Cleanup Error")
         return False

  def check_process(self):
      cmd = 'ps -ef | grep haops.py | grep ' + self.name + ' | grep -v grep  | grep -v ' + str(self.pid)
      if self.run_command(cmd) == 0:
         self.log(1, "check_process", "Another instance started")
         return False
      else:
         self.log(1, "check_process", "Ready to start")
         return True

  def check_failcount(self):
      cmd = "pcs resource failcount show " + self.name +  " | grep INFINITY"
      if self.run_command(cmd) == 0:
         self.log(0, "check_failcount", "Failcount Infinity")
         return True

      else:
         self.log(0, "check_failcount", "Failcount OK")
         return False

  def run_command(self, cmd):
      status,output = commands.getstatusoutput(cmd)
      self.log(2, "command.cmd", cmd)
      self.log(2, "command.return", str(status))
      self.log(2, "command.output", output)
      return status

  def log(self, level, action, code):
      if self.debug >= level:
         msg = "hamonitor (" + str(self.pid) + ") operation \'" + action + "\' for \'" + self.name + "\' on \'" + self.node + "\': " + code
         now = datetime.now()
         open(self.logfile, 'a').write(now.strftime("%b %d %H:%M:%S.%f: ") + msg + "\n")

if (len(sys.argv) != 5 ):
   print "Invalid arguments"
   exit()
 

hamonitor = hamonitor(sys.argv[1], sys.argv[2], sys.argv[3], sys.argv[4])
hamonitor.run()
{% endhighlight %}
