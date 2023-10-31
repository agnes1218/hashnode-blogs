---
title: "Day 73 - Grafana 🔥"
datePublished: Tue Oct 31 2023 16:54:40 GMT+0000 (Coordinated Universal Time)
cuid: cloekk4na00080aif5wxd544z
slug: day-73-grafana
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1698771242178/2cc6141c-61f3-4ac1-bd75-21ecd66f4a0c.png
tags: monitoring, devops, grafana, 90daysofdevops, trainwithshubham

---

Task:

> Setup Grafana in your local environment on AWS EC2.

1. Navigate to the AWS console, and create an EC2 instance named “grafana”
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698768280902/0e7c8dae-b0a3-4cc8-bfb5-2656b9848f01.png align="center")

1. SSH console and login into the machine.
    
2. Download the GPG keys and add them to the trusted keys list.
    

“wget -q -O - [https://packages.grafana.com/gpg.key](https://packages.grafana.com/gpg.key) | sudo apt-key add”

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698768697212/b9b60116-31ae-4246-bdee-5461ec136772.png align="center")

1. Add it to the Grafana repository.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698768854802/5e71fe47-f3e6-4ef8-b80e-2124d6f9a6c5.png align="center")
    
2. We need to update the system. “`sudo apt update`”
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698769022228/f6e6099f-f1f5-4cc0-ab01-8e214db728ef.png align="center")

1. we need to install the Grafana.
    
    `“sudo apt install grafana”`
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698769291171/e08bd6b9-a357-4967-a2cf-5482c8c3bde3.png align="center")
    
    1.   After installation, add Grafana to auto-start and start the Grafana daemon itself.
        
        “sudo systemctl enable grafana-server”
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698769410654/91da3368-0321-42ec-95d2-f323d23756d9.png align="center")
        
        “sudo systemctl start grafana-server”
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698769475733/9025887a-dc72-4be7-b1d3-583b7265d169.png align="center")
        
    2. Installation of the Grafana repo is finished and ready to use. Now, check the status. As
        
        “`sudo systemctl status grafana-server`”
        
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698769581438/6f6186ac-c38e-4a9d-a867-057720524eba.png align="center")
    

1. Now, go to the browser and search with,
    
    “&lt;IP\_of\_EC2:3000&gt;”
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698770957886/29c94b12-39e4-4997-b0a5-f0eacb2cd6a5.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698770981401/e9ba3d0d-5438-4796-b010-38fadd9ddb19.png align="center")

1. By default, username and password are set to admin admin
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698771055215/dafd8ed8-49a3-43b6-ba04-6fea225117bb.png align="center")
    

Let's explore Grafana more in the next blog.

***Happy Learning!***