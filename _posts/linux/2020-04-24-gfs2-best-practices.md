---
layout: post
title:  "GFS2 best practices"
date:   2020-04-24 08:30:52 -0400
img: linux.png
categories: Linux
tags: Clustering
---

![Linux]({{site.baseurl}}/images/linux.png)


### GFS2 File system size
In general, GFS2 is that smaller is better. It will have less resource groups to maintain mean better performance, it will also take less time for backup/check if needed. However, if you make your GFS2 file system too small, you might run out of space. You should consider your own use cases before deciding on a size

## Journals
Number of Journals should be one for each node that mounts. For example, if you have a 6-node cluster but only need to mount the file system from two nodes, you only need two Journals. You can add journals on the fly.

It is a general best practice to use the default journal size of 128MB. If your file system is very small (for example, 5GB), having a 128MB journal might be impractical. If you have a larger file system and can afford the space, using 256MB journals might improve performance.
 
### Number and size of Resource Groups
Too many resource groups (each of which is small) will waste time searching resource groups for free blocks for allocations. Too few resource groups (each of which is big) might contend more often for the same resource-group lock.

When GFS2 is created with mkfs.gfs2, it will choose the resource group size based on the size of the target file system. But it does not always select the best value for your application, you can override by specifying the -r option.

### Block Allocation
*  Leave Free Space in the File System

If file system is close to full,  block allocator will spend time finding free new blocks and cause file fragmentation. It is recommended that you not run a file system that is more than 85 percent full, although this figure may vary depending on workload.

* Have Each Node Allocate Its Own Files, If Possible

With DLM, the first node to lock a resource (like a file) becomes the “lock master” for that lock. Other nodes may lock that resource, but they have to ask permission from the lock master first. As a result, it will be more lock contention if all files are allocated by one node and other nodes need to add blocks to those files.

* Preallocate, If Possible

If files are preallocated, block allocations can be avoided altogether and the file system can run more efficiently. You can use fallocate to preallocate blocks of data.

### Glock contention
* The inode glocks and the resource group glocks both cache metadata 
* Avoid file glock contention, use glocktop to verify if many processes waiting for inode glocks. 
* Avoid multiple GFS2 nodes writing the same file, 
* Avoid directory contention by having each GFS2 node has its own directory to write data
* Verify GFS2 lock dump caused by backup or other search activities. See Red Hat Documentation for details
* Verify if you have too many small files. GFS2 does not performance well when millions of small files placed in the same directory

### Other system configurations
* Ensure the OS is patched to the latest to avoid past GFS2 bugs related to performance
* Use noatime mount option to turn off writing the last access time
* Default block size 4k is preferred
* Disable SELinux to avoid additional overhead with extended attributes (such change is considered insignificant by Red Hat right now)
 
### Make a plan for backup
Since backing up a node usually involves reading the entire file system in sequence. The node will retain all the information in cache until other nodes in the cluster start requesting locks. Running this type of backup program while the cluster is in operation will negatively impact performance.  

Dropping the caches once the backup is complete reduces the time required by other nodes to regain ownership of their cluster locks/caches. This is still not ideal, however, because the other nodes will have stopped caching the data that they were caching before the backup process began. You can drop caches using the following command after the backup is complete:

echo -n 3 > /proc/sys/vm/drop_caches

It is faster if each node in the cluster backs up its own files so that the task is split between the nodes. No commercial backup software operates that way, but you might be able to accomplish the same thing with a script that uses rsync on node-specific directories.

The best way for GFS2 backup is to create a hardware snapshot on the SAN, present the snapshot to another system, and back it up there. The backup system should mount the snapshot with -o lockproto=lock_nolock since it will not be in a cluster. 

