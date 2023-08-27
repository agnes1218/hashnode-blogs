---
title: "Day5 Advanced Linux Shell Scripting"
datePublished: Sun Jul 23 2023 16:52:55 GMT+0000 (Coordinated Universal Time)
cuid: clkfogpb300000ajr9nnjhepe
slug: day5-advanced-linux-shell-scripting
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1690131087645/19e456f0-30fb-4cf7-81c1-5f5728dbe89a.png
tags: linux, devops, shell-scripting, trainwithshubham, 90daysofdevops-chanllenge

---

Today's blog will cover advanced shell scripting with reference to the previous blog we have already covered the Linux shell scripting basic. The Bash Shell Script that is written with #!/bin/bash (Shebang) specifies that the script should be interpreted and executed by the Bash Shell.

**Variables in Shell Script**

Variables are used to store data temporarily. To get the value of a variable, the variable name is prefixed with a dollar sign ($).

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690121967352/157e9df0-bd4e-41db-8996-6bbcdddc757d.png align="left")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690122129166/707a9c89-018c-45a8-985c-31ad961aeba1.png align="left")

**Arguments in Shell Script**

Shell Script can take the arguments that are passed when executing the script from the command prompt.

Syntax -

./&lt;scriptfile\_name&gt; arg1 arg2

special variables are $0, $1, $2

* $0 - The name of the scripts
    
* $1 - First argument that is passed from the command line.
    
* $2 - Represents the second argument.
    

**Task 1** -

The script is executed with three given arguments (one is the directory name and second is the start number of directories and the third is the end number of directories ) it creates a specified number of directories with a dynamic directory name.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690123372611/f4413993-e32e-4feb-8628-59a1e142fd13.png align="left")

After the execution of the script, will create 90 directories.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690123549210/16d141cd-19a9-451c-98d4-2dc9e08be67b.png align="left")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690123842760/58423768-9d95-422f-a86d-cc85583d4123.png align="center")

Task 2 - Backup all the works

Backups are an important part of DevOps Engineers' day to Day activities. To save the file from unnecessary failure, backup ensures data recovery and automates data safety.

We will take backup by compressing and archiving a source and target directory location. `tar` the command helps to compress and archive the file with options

\-c -Creates Archive **\-v :** Displays Verbose Information **\-f :** creates archive with given filename 

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690128126236/5e01f4a3-e8da-42cc-95ca-84aa5c6d617a.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690127932507/a96df0fd-7c59-4e1c-8f5e-7b67d602fc90.png align="left")

The backup is stored in the target directory.

**Cron and Crontab, to automate the backup Script**

`Cron` is a time-based task scheduler. We will automate the above backup script to run at specific intervals of time.

`crontab` is a file containing all schedules of the cron jobs a user wants to run regularly.

* First, use the crontab command to create your first crontab
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690128941262/4fcb2b9a-7410-4bb2-b77a-24f4baa9051b.png align="center")

Enter the values based on below values

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690129674239/8ed1402a-1f2a-4322-954c-c8fa00927cd7.png align="left")

```bash
5 * * * * cat /path/to/your/backup.sh  - Replace you script path with actual backup.sh path
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690129881745/5f1cbd98-ea51-42ab-8fa7-1977ea1f9af6.png align="center")

The backup will automatically run at a given specific time.

## **User Management**

A user is an entity, in a Linux operating system, that can manipulate files and perform several other operations. Each user is assigned an ID that is unique for each user in the operating system.

`Useradd` **- To create a User.**

`userdel` - To delete a user

`usermod` - To modify user properties

`id` - To display user information

In the below task, we will create 2 users and display their names.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690130642058/fe930911-4821-4ab2-8e16-81dc4a5ec4a9.png align="center")

The command will fetch the usernames from /etc/passwd

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690130701639/673021ab-a1a7-4c82-9332-7d289f232db3.png align="left")

Thank you for reading!

Let's continue this exciting journey of DevOps together.

*Happy Learning!*