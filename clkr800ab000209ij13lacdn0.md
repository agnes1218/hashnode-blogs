---
title: "Day 14 Task: Python Data Types and Data Structures for DevOps"
datePublished: Mon Jul 31 2023 18:45:16 GMT+0000 (Coordinated Universal Time)
cuid: clkr800ab000209ij13lacdn0
slug: day-14-task-python-data-types-and-data-structures-for-devops
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1690829037664/330fb9c7-2304-4ddf-85d9-4eff514de88e.png
tags: python, devops, 90daysofdevops, day14, trainwithshubham

---

### Data Types

* Data types are the classification or categorization of data items. It represents the kind of value that tells what operations can be performed on a particular data.
    
* Since everything is an object in Python programming, data types are actually classes and variables are instances (objects) of these classes.
    
* Python has the following data types built-in by default: Numeric(Integer, complex, float), Sequential(string,lists, tuples), Boolean, Set, Dictionaries, etc
    

To check what is the data type of the variable used, we can simply write: `your_variable=100` `type(your_variable)`

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690820616539/0617589f-354f-4f0a-81df-0a3d3e330a3c.png align="center")

### Data Structures

Data Structures are a way of organizing data so that it can be accessed more efficiently depending on the situation. Data Structures are fundamentals of any programming language around which a program is built. Python helps to learn the fundamental of these data structures in a simpler way as compared to other programming languages.

* **Lists** Python Lists are just like the arrays, declared in other languages which is an ordered collection of data. It is very flexible as the items in a list do not need to be of the same type
    
* **Tuple** Python Tuple is a collection of Python objects much like a list but Tuples are immutable in nature i.e. the elements in the tuple cannot be added or removed once created. Just like a List, a Tuple can also contain elements of various types.
    
* **Dictionary** Python dictionary is like hash tables in any other language with the time complexity of O(1). It is an unordered collection of data values, used to store data values like a map, which, unlike other Data Types that hold only a single value as an element, Dictionary holds the key: value pair. Key-value is provided in the dictionary to make it more optimized
    

## Task 1:

1. Give the Difference between List, Tuple, and Set. Do Handson and put screenshots as per your understanding.
    
    **List:** A list is a collection of items that are ordered and changeable. Lists are written with square brackets and items are separated by commas. Lists can contain any type of item, including other lists.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690822994114/fe323637-3006-4253-8afb-c19efedefeb7.png align="left")
    
2. **Tuple:** A tuple is a collection of items that are ordered and unchangeable. Tuples are written with parentheses and items are separated by commas. Tuples can contain any type of item, including other tuples.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690823862162/47580140-9525-46b8-abc1-0ef50c0f027d.png align="left")
    
3. **The set** is an unordered collection of data types that is iterable, mutable, and has no duplicate elements. The order of elements in a set is undefined though it may consist of various elements.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690823892898/c7fd23be-eaf5-48b1-b4d9-16ca057bf37d.png align="left")

**Task 2 :**

2. Create the below Dictionary and use Dictionary methods to print your favorite tool just by using the keys of the Dictionary.
    
    ```bash
    fav_tools = 
    { 
      1:"Linux", 
      2:"Git", 
      3:"Docker", 
      4:"Kubernetes", 
      5:"Terraform", 
      6:"Ansible", 
      7:"Chef"
    }
    ```
    
    To print the values of all the keys in the above dictionary, I used for loop and iterate the keys to get all the values.
    
    **for i in fav\_tools:**
    
    **print(fav\_tools\[i\])**
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690824841117/1fc640f0-695d-40d9-894c-fc73c40a6b69.png align="left")
    
    To Print the fav\_tool
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690824982792/e84d07ec-2f1e-4fe7-9eac-919ae1aa72da.png align="left")
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690825027849/57752180-5662-41f7-9ce7-4be7d1dc6b27.png align="left")
    
    **Task - 3: Create a List of cloud service providers**
    
    ```bash
    cloud_providers = ["AWS","GCP","Azure"]
    ```
    
    Write a program to add `Digital Ocean` to the list of cloud\_providers and sort the list in alphabetical order.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690827586359/7a91d9ef-b9ff-4ac7-b56d-89382a31b404.png align="left")
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690827619161/201cc172-43a7-4335-94ce-b17cb799fe22.png align="center")
    
    **This is the** [**#90DaysofDevops**](https://www.linkedin.com/feed/hashtag/?keywords=90daysofdevops&highlightedUpdateUrns=urn%3Ali%3Aactivity%3A7015419431497416704) **challenge under the guidance of** @[Shubham Londhe](@TrainWithShubham).
    

**Thank you for reading!**