---
title: "Day 15 Task: Python Libraries for DevOps"
datePublished: Wed Aug 02 2023 07:00:13 GMT+0000 (Coordinated Universal Time)
cuid: clktdozx1000v09l62qg3fhms
slug: day-15-task-python-libraries-for-devops
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1690959549521/64bdf852-16a3-481d-9cd8-4c6c20397da3.png
tags: python, devops, python-libraries, trainwithshubham, 90daysofdevops-chanllenge

---

Python day-to-day tasks

## Tasks

1. Create a Dictionary in Python and write it to a JSON File
    
    simply create a dictionary in Python and convert this Python object into JSON object and write into the JSON file.
    
    Json.dumps() - convert the python object into an equivalent JSON object and stores the result into a JSON file at the working directory.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690955641017/05bd1604-d096-4630-aae6-29100cfc340e.png align="left")
    
2. Read a JSON file `services.json` kept in this folder and print the service names of every cloud service provider.
    
    json.load() : A Python dictionary is created and it is returned via the json.load() function.
    

```bash
output

aws : ec2
azure : VM
gcp : compute engine

```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690957372908/b0aa32be-a1b4-4cc2-82bf-ffbf09b3091d.png align="center")

1. Read YAML file using python, file `services.yaml` and read the contents to convert yaml to json
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690958706661/de1fb19a-9cb4-4891-b295-3857472754d4.png align="center")

1. Install PyYAML with pip install
    
2. import yaml statement will import the module.
    
3. the open method will view the file
    
4. yaml.safe\_load() - Prases the given and returns a python object constructed from the first document in the stream.
    

Thank you for reading this article!

**Happy Learning!**