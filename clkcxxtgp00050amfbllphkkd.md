---
title: "Day 7 -Package Manager in Linux"
datePublished: Fri Jul 21 2023 18:54:52 GMT+0000 (Coordinated Universal Time)
cuid: clkcxxtgp00050amfbllphkkd
slug: day-7-package-manager-in-linux
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1689965579186/76ab834e-35c1-4af4-87ba-a5d1bb166b47.png
tags: linux, devops, hashnode, 90daysofdevops, trainwithshubham

---

In this Blog, we will cover the package Manager and Sytemctl.

### Package Management

The package manager can be a graphical application like a software center or a command line tool like apt-get or Pacman. A package manager is a tool that allows users to install, remove, upgrade, configure, and manage software packages on an operating system.

### What is a package?

In Linux, a package is a format that contains all the necessary files and information that are required to install and manage a specific application.

### **Different kinds of package managers:**

Package Managers differ based on the packaging system but the same packaging system may have more than one package manager.

**APT (Advanced Package Tool) - APT is a** command-line tool, which works with Ubuntu’s Advanced Packaging Tool (APT).

Some examples use for the `apt` utility include:

* `sudo apt-get install package_name` \- Install the Package
    
* `sudo apt-get update` followed by `sudo apt-get upgrade` \- Update the Package
    
    **YUM (YellowDog update Manager)** - YUM provides a command-line interface for managing packages in RHEL.
    
* `sudo yum install package_name` - Install the package
    
* `sudo yum update` & `sudo apt-get upgrade` - Update the Package
    
* `sudo yum remove package_name` - Remove the Package
    

**RPM (Red Hat Package Manager) -** It is an open-source package manager (default) and the most famous utility of package management for Red Hat-based systems such as Fedora, CentOS, and RHEL.

*  `sudo apt install rpm` - Install the Package
    

Below is some example of installing Docker & Jenkins using Package Manager.

**Installing Docker on Ubuntu using APT**

1. Open the terminal on Ubuntu
    
2. Check if the system is up-to-date
    

* sudo `apt` update
    
* ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689959014531/e4f7554b-8ecf-4399-8c9c-ebea324ce43f.png align="left")
    
    3\. Install Docker using the following command
    
* sudo `apt-get install` [docker.io](http://docker.io) -y
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689959887648/940e3918-035e-4439-a9c3-8d08ccd8e9a1.png align="left")
    
    check the version installed using the following command: **docker --version**
    
* ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689960596396/bf77e18f-776c-4a96-ac39-39f1eeec4719.png align="left")
    

**Install Jenkins with Ubuntu**

**Step 1: Install Java**

Jenkins requires the Java Runtime Environment (JRE).

1.  `java --version` **To check the latest Java version if java is already installed on system.**

2\. Install OpenJDK 8, : `sudo apt install openjdk-8-jdk -y`

install OpenJDK 11, run: `sudo apt install openjdk-11-jdk -y`

**Step 2 : Add Jenkins**

1\. Import GPG Key by using the below command

The GPG key verifies package integrity but there is no output.

```bash
curl -fsSL https://pkg.jenkins.io/debian/jenkins.io-2023.key | sudo tee \
  /usr/share/keyrings/jenkins-keyring.asc > /dev/null
echo deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc] \
  https://pkg.jenkins.io/debian binary/ | sudo tee \
  /etc/apt/sources.list.d/jenkins.list > /dev/null
```

**2\. Update and install the Jenkins**

`sudo apt update`

`sudo apt install jenkins -y`

**Step 3** : **Stop the service jenkins and post before and after screenshots.**

Before:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689964525835/9991d5dd-46e0-48a1-9af0-3a2e4f7d2bf0.png align="center")

After:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689964618723/64a331f4-17a2-4f24-b9f2-2b7cf8de3938.png align="center")

Task 3:

`systemctl` and `service` are both commands used to manage services in Linux, but they have some differences in their functionality and usage.

`systemctl :` The **systemctl** command interacts with the SystemD service manager to manage the services.

`services`: It manages the services by interacting with the SystemD process.

It provides controlling services like Start,Stop,restart, enable, disable.

`systemctl start jenkins` \- Is a command to start the Jenkins services.

`Service jenkins status` \- Is a command to check the status of Jenkins Services.

Thankyou for reading this Blog.

*Happy Learning!*