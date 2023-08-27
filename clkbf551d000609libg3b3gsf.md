---
title: "Day 6 -Linux File Permission and Access Control List"
datePublished: Thu Jul 20 2023 17:20:54 GMT+0000 (Coordinated Universal Time)
cuid: clkbf551d000609libg3b3gsf
slug: day-6-linux-file-permission-and-access-control-list
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1689869452779/ac4c2782-37ff-474d-88af-8a580d13652f.png
tags: linux, devops, 90daysofdevops, trainwithshubham, 90daysofdevopschallenge

---

The most important factor for every organization is security. Linux is widely known for its security factor.

Linux ensures security and control over sensitive data (files ) & directories. Linux allows administrators to manage the access for users and groups.

To understand file permission we will create a simple file

* `touch` test.txt - Create a file with the touch command
    
* `ls -ltr` to see the details of the files
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689870850885/4ded4849-c39f-4391-a809-e29a1305b882.png align="center")

Two important mechanisms that Linux provides are:

* File permission
    
* Access control list
    
    # Linux File Ownership
    

**Users**: the user is the owner of the file and the application

* "`chown`" is used to change the ownership permission of a file or directory.
    

**Group**: Groups that own the file and applications.

* "`chgrp`" is used to change the group permission of a file or directory.
    

**Other**: All users with access to the system.

others — All users with access to the system. (outside the users are in a group)

### There are three kinds of file permissions in Linux:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689870034863/fe5d0693-7432-4ad4-a3fa-d1d14ca5241f.png align="left")

* `Read` (r): Allows a user or group to view a file.
    
* `Write` (w): Permits the user to write or modify a file or directory.
    
* `Execute` (x): A user or group with execute permissions can execute a file or view a directory.
    

Permission numbers are:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689871711435/53ee3087-9441-445f-b2aa-651e219e276e.png align="left")

* 0 = ---
    
* 1 = --x
    
* 2 = -w-
    
* 3 = -wx
    
* 4 = r-
    
* 5 = r-x
    
* 6 = rw-
    
* 7 = rwx
    

For example:

* chmod 777 folder name will give read, write, and execute permissions for everyone.
    
* chmod 700 folder name will give read, write, and execute permissions for the user only.
    

**Task** :

change the user permissions of the file and note the changes after `ls -ltr`

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689871484957/b3fab71c-fd93-493d-a377-dfe8488f35f7.png align="left")

The above task changed the file permission to execute.

### **Access Control List**

ACL is a service that is used for providing special permission to specific Users & Groups for particular files and directories. ACLs can set read, write, and execute permissions for the owner, group, and other users.

`getfacl` - To check the Access Control permission.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689872789038/343dba8f-ac7d-4451-bbc5-c74c4e44559c.png align="center")

`setfacl` - command is used to set ACL permission.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689872961317/a7240093-565f-477b-a54d-b2f2924f96a6.png align="center")

In the Above task set ACL permission to the user.

Thank you for reading this blog.

*Happy Learning!*