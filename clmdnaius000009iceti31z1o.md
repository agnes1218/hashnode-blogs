---
title: "Day 45: Deploy WordPress website on AWS"
datePublished: Sun Sep 10 2023 16:03:59 GMT+0000 (Coordinated Universal Time)
cuid: clmdnaius000009iceti31z1o
slug: day-45-deploy-wordpress-website-on-aws
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1694361811053/f98cdf5a-2023-4308-9b6e-c9756528bd61.png
tags: aws, wordpress, devops, 90daysofdevops, trainwithshubham

---

Over 30% of all websites on the internet use WordPress as their content management system (CMS). It is most often used to run blogs, but it can also be used to run e-commerce sites, message boards, and many other popular things. This guide will show you how to set up a WordPress blog site.

## Task-01

* **As WordPress requires a MySQL database to store its data, create an RDS as you did on Day 44**
    

Go to the Amazon RDS console. Click "Create database".

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694358256485/009d2357-5af9-4732-bd54-3023a10adb1d.png align="center")

Choose the "Free tier" template for the "DB instance class".

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694358320581/399b7aa1-c3be-4760-a8d8-46639fa19bdd.png align="center")

Enter a unique name for the "DB instance identifier".

Set the "Master username" and "Master password" for the database.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694358359656/f8a0c507-e3c3-40d0-94d3-e10160d66886.png align="center")

Set the "Virtual Private Cloud (VPC)" and "Subnet group" to create the instance in. Leave the other settings at their default values.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694358407360/8b36fc0a-5f94-4ed0-a1fb-8a328deaf4ff.png align="center")

Choose 'Default VPC'

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694358480415/80364981-509d-4041-a5bb-c95ce03f5c6b.png align="center")

Click on "Create database"

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694358545202/d0a6b12f-c8a3-49cf-9a5c-6eca23d64d49.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694358941493/690bc880-dcff-4883-bc77-f8521ef895e0.png align="center")

### **To configure this WordPress site, you will create the following resources in AWS:**

**An Amazon EC2 instance to install and host the WordPress application.**

Go to the Amazon EC2 console., Click "Launch Instance" and choose a Linux AMI.

Choose an instance type, such as t2. micro, Choose a VPC and subnet.

Configure security group rules to allow inbound traffic on the appropriate port for the type of database you are using (e.g. port 3306 for MySQL).

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694359048177/317a8735-64c1-4b0a-8db7-fe5eaded53e0.png align="center")

### **An Amazon RDS for MySQL database to store your WordPress data.**

Choose the MySQL database you created, go to the Connectivity & Security tab in the display, and choose the security group listed in VPC security groups. The console will take you to the security group configured for your database.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694359646054/b3541a97-d1ff-4cfc-9c4c-6b34a9ccd7b6.png align="center")

Select the Inbound Rules tab, then choose the Edit inbound rules button to change the rules for your security group.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694359734714/b3b34538-dda1-45d9-949c-137548bc34c9.png align="center")

Change the Type property to MYSQL/Aurora, which will update the Protocol and Port range to the proper values.

Choose the security group that you used for your EC2 instance.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694359806647/15fc9a83-5059-4b06-bfd0-836ba551af0f.png align="center")

SSH into your EC2 instance

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694359952195/fe740225-cb52-4b2b-a820-3bf272a84f77.png align="center")

run the following command in your terminal to install a MySQL client to interact with the database.

```yaml
sudo apt install mysql-client
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694360255223/4a2656a1-f5eb-4ec7-9906-2dcd4e4d645c.png align="center")

Run the following command in your terminal to connect to your MySQL database. Replace “&lt;user&gt;” and “&lt;password&gt;” with the master username and password you configured when creating your Amazon RDS database. -h is host which is RDS database endpoint.

![No alt text provided for this image](https://media.licdn.com/dms/image/D4D12AQEBDMZ62YMOQA/article-inline_image-shrink_1500_2232/0/1677058928498?e=1700092800&v=beta&t=cMZhmoihrdkSrpUhTBb0I-1DKncQBkXSWF6ohU0p1k8 align="left")

Finally, create a database user for your WordPress application and give the user permission to access the wordpress database.

Run the following commands in your terminal:

```yaml
CREATE DATABASE wordpress;
CREATE USER 'wordpress' IDENTIFIED BY 'wordpress-pass';
GRANT ALL PRIVILEGES ON wordpress.* TO wordpress;
FLUSH PRIVILEGES;
Exit
```

To run WordPress, you need to run a web server on your EC2 instance.

To install Apache on your EC2 instance, run the following command in your terminal:

```yaml
sudo apt-get install apache2
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694361312458/dd22ad11-8bab-4f21-b0e1-a2320627b2e4.png align="center")

To start the Apache web server, run the following command in your terminal:

```yaml
systemctl restart apache2
```

You can see that your Apache web server is working by browsing the public IP of your ec2 instance.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694361501691/45d2e683-cb14-430b-95d2-fe75e33c48b1.png align="center")

**Setup the server and post your new Wordpress app.**

First, download and uncompress the software by running the following commands in your terminal:

```yaml
wget https://wordpress.org/latest.tar.g
tar -xzf latest.tar.gzz
```

![No alt text provided for this image](https://media.licdn.com/dms/image/D4D12AQGY14d0z0dqIA/article-inline_image-shrink_1500_2232/0/1677059023830?e=1700092800&v=beta&t=duViiNFxWw7GxveDG_rrNUe0VhQoaklVNSCDIx__dPg align="left")

Change the directory to the WordPress directory and create a copy of the default config file using the following commands

open the wp-config.php file

![No alt text provided for this image](https://media.licdn.com/dms/image/D4D12AQFErb57WI9Vwg/article-inline_image-shrink_1500_2232/0/1677059081465?e=1700092800&v=beta&t=J0p59LbOylhA4qOJEBgphTxmo26VPRdafZb0Xbucaro align="left")

Edit the database configuration by changing the following lines:

![No alt text provided for this image](https://media.licdn.com/dms/image/D4D12AQFbjjBlKKrEYg/article-inline_image-shrink_1500_2232/0/1677059094445?e=1700092800&v=beta&t=rVy4pn1JB03UR8L997X-Xs-4Us7vEz0SNugpVwWHjCE align="left")

The second configuration section you need to configure is the Authentication Unique Keys and Salts.

You can replace the entire content in that section with the below content:

![No alt text provided for this image](https://media.licdn.com/dms/image/D4D12AQHwnPtKNumtuw/article-inline_image-shrink_1500_2232/0/1677059106990?e=1700092800&v=beta&t=h_aHjGqqlFzw363fa76E9v265WUAt4HCUNQg8tp9F8E align="left")

install the application dependencies you need for WordPress. In your terminal, run the following command.

```yaml
sudo apt install php libapache2-mod-php php-mysql -y
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694361663401/6cbfd37d-21aa-44c9-8663-6bd45f327b34.png align="center")

Copy your WordPress application files into the /var/www/html directory used by Apache.

```yaml
sudo cp -r wordpress/* /var/www/html/
```

Finally, restart the Apache web server

```yaml
systemctl restart apache2
```

Browse "ec2-public-ip/wp-admin/" you should see the WordPress welcome page.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694361737918/ef3a767b-bfbd-45dc-99e0-5a3a57d47978.png align="center")

***Happy Learning!***