---
title: "Day 74 - Connecting EC2 with Grafana ."
datePublished: Thu Nov 02 2023 17:10:35 GMT+0000 (Coordinated Universal Time)
cuid: clohg0b4f000109l466lbckhs
slug: day-74-connecting-ec2-with-grafana
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1698944985885/dd0afb94-9781-434f-9179-4454652937d4.png
tags: monitoring, devops, 90daysofdevops, trainwithshubham, grafana-monitoring

---

**Task:**

Connect a Linux and one Windows EC2 instance with Grafana and monitor the different components of the server.

1. ## **Setup Grafana**
    
2. ## **Install Docker:**
    
    Updates the package lists on the system, ensuring that the latest package information is available for installation.
    
    ```plaintext
    sudo apt-get update
    sudo apt install docker.io
    sudo usermod -aG docker $USER
    sudo reboot
    ```
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698942072351/f286629c-77cb-4743-bdf0-9d4c6176cc93.png align="center")
    
    3\. **Download Loki Config:**
    
    Use the following command to download the Loki configuration file:
    
    ```plaintext
    mkdir grafana_configs
    cd grafana_configs
    wget 
    https://raw.githubusercontent.com/grafana/loki/v2.8.0/cmd/loki/loki-local-config.yaml -O loki-config.yaml
    ```
    
    * This command uses `wget` to download the Loki configuration file from the specified URL.
        
    * The configuration file contains settings for Loki, such as storage configurations, retention policies, and remote storage options.
        
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698942163643/9dcb477b-1480-4407-b86e-2ff29a4bcb72.png align="center")

## **Download Promtail Config**

Download the Promtail configuration file using the command below in grafana\_configs directory:

```plaintext
wget 
https://raw.githubusercontent.com/grafana/loki/v2.8.0/clients/cmd/promtail/promtail-docker-confi
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698942283152/2db1a113-645d-459e-94ad-1dd7a5529b8d.png align="center")

## **Run Loki Docker container:**

Execute the following command to run the Loki Docker container, providing the downloaded configuration file:

```plaintext
sudo docker run -d 
--name loki -v $(pwd):/mnt/config -p 3100:3100
grafana/loki:2.8.0 --config.file=/mnt/config/loki-config.yaml
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698942442009/af0bc009-8200-4181-a4c6-99f2d9079978.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698942483808/24b232b9-fd58-4a88-8b5e-7fb3b181f830.png align="center")

* Edit the inbound rule in the security group of the ec2 instance to allow port 3100.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698942572769/a1e08739-10d5-43e2-b694-12636119b417.png align="center")

* Copy public-ip of instance and paste in browser on https:&lt;public-ip&gt;:3100/ready and check loki is ready..?
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698942645784/589d0501-7121-4550-87ac-540b2178262d.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698942781690/d3cbcfca-772c-4fee-bc53-fc358c1503b7.png align="center")

* In Loki what kind of logs or metrics are there we can get those like this use `/metrics`\`
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698942826338/ceac7f9b-5ef8-4ed8-a91b-d10ddf12d6a5.png align="center")

## **Run Promtail Docker container:**

Run the Promtail Docker container with the downloaded configuration file, mounting the host’s log directory:

```plaintext
sudo docker run -d --name promtail -v $(pwd):/mnt/config -v /var/log:/var/log 
--link loki grafana/promtail:2.8.0 
--config.file=/mnt/config/promtail-config.yaml
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698942919170/241a6d11-2419-4cf7-ad5a-a67dbe7e1968.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698943037988/87287f2d-ac0d-45d0-bf6d-f767dc10f16d.png align="center")

## **\- Add Data source in Grafana**

* Now, navigate to the Grafana web app and on the homepage choose the add data source option.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698943204805/c5071573-8d90-45d1-a951-20b5d9a5c449.png align="center")
    
    * Provide the HTTP URL as below to connect the loki data source to Grafana so that loki will send the logs to grafana.
        
    * [*localhost:3100*](http://localhost:3100)
        
    * Click on save & test to connect the data source.
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698943283602/a28a7a3a-17f3-43b5-9231-b2a1243ac29a.png align="center")
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698943294783/c1e8ac50-bf41-4242-8335-123a83b6286f.png align="center")
        

# **Checking logs in Loki:**

* Click on explore in the below screenshot after adding the data source.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698943350786/30ffbcc7-eb7d-4112-98b2-0882bc932297.png align="center")
    

Run Query will display below output

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698943409723/2d6ad442-217e-404a-9eaf-c2ef0ffbc26d.png align="center")

# **Create Dashboard:**

* Let’s add the log to the dashboard by choosing the option from the above screenshot location.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698943475743/d3e28d81-6250-4da7-b35f-f6f8f22b9d2e.png align="center")

* In Label filters choose job and varlogs and line contains to error to show all the lines Run Query.
    
* On right hand side choose Logs &gt; Click to change visualization&gt; select row format as shown in below.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698943530411/67815e5e-0137-494b-b7ba-39594772a075.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698943625649/fa2e44be-ad0d-4891-a1b0-bde0f09696c9.png align="center")

**let’s check the error lines in grafana log that is placed in */var/log/grafana/grafana.log***

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698943754959/abc7e032-2064-4c75-804b-bebd332f47d4.png align="center")

To display the Grafana log, we must specify the Grafana log path in the promtail config YAML file within the target section, as illustrated below.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698943967634/362a1614-51f1-4475-bdb0-de3d9798acf8.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698944109406/8647c422-f323-4b2a-8a19-fd0cdb4dfc62.png align="center")

* After editing promtail\_config.yaml file we have to restart our promtail docker container
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698944170587/4ad39588-0044-40d1-96b2-42b5057904db.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698944314833/9788d5b2-807f-4483-9ecd-1445d5e7bec4.png align="center")

* Use the proper label filters to show an aggregate sum of words repeating nginx while installing. This can be achieved by setting the varlogs as label filters.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698944666624/6f442444-7093-42f2-9c69-2b66a3838976.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698944803402/ef3afd7c-7d18-4103-a8ab-c8c9e7d13697.png align="center")

***Happy Learning!***