---
title: "Day 72 - Grafana🔥"
datePublished: Mon Oct 30 2023 16:22:12 GMT+0000 (Coordinated Universal Time)
cuid: clod3yj6s000009jj2jcdc3iz
slug: day-72-grafana
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1698682903319/6b986979-03df-40c5-b739-53f639aefe71.png
tags: devops, prometheus, grafana, 90daysofdevops, trainwithshubham

---

## [Task 1:](https://github.com/agnes1218/90DaysOfDevOps/blob/master/2023/day72/tasks.md#task-1)

### What is Grafana?

Grafana is an open-source data visualization and monitoring tool that allows you to query, visualize, alert on, and understand your metrics no matter where they are stored. It supports a wide range of data sources, including popular databases like MySQL, PostgreSQL, and Prometheus.

### **What are the features of Grafana?**

Some of the key features of Grafana include:

1. A powerful and flexible dashboard editor that allows you to create dynamic, responsive, and visually appealing dashboard.
    
2. Support for multiple data sources, including databases, time series databases, and log data.
    
3. A variety of visualization options, including graphs, tables, gauges, and heat maps.
    
4. Alerting capabilities that allow you to set up rules and notifications based on specific metrics or conditions.
    
5. User management and access control features that allow you to control who has access to your dashboards and data sources.
    
6. A large and active community that provides support and contributes to the development of the platform.
    

### **Why Grafana?**

Grafana is a popular choice for data visualization and monitoring due to its powerful and flexible dashboard editor, support for multiple data sources, variety of visualization options, alerting capabilities, user management features, and active community support. It allows users to quickly and easily create dynamic, responsive, and visually appealing dashboards that can help them gain insights into the performance and health of their systems. Additionally, Grafana can be integrated with a wide range of data sources, including databases, time series databases, and log data, making it a versatile tool for monitoring and visualization of various systems.

### **What type of monitoring can be done via Grafana?**

Grafana supports a wide range of monitoring types, including:

1. **Infrastructure Monitoring:** Grafana can be used for monitoring the health and performance of infrastructure components such as servers, databases, and networks.
    
2. **Application Monitoring:** Grafana can be used to monitor application performance metrics such as response time, error rates, and throughput.
    
3. **Log Monitoring:** Grafana can be used to analyze logs and create visualizations of log data to identify trends, patterns, and anomalies.
    
4. **IoT Device Monitoring:** Grafana can be used to monitor and visualize data from IoT devices, such as temperature sensors, humidity sensors, and motion sensors.
    
5. **Business Metrics Monitoring:** Grafana can be used to monitor business metrics such as sales figures, revenue, and customer satisfaction.
    

### **What databases work with Grafana?**

Grafana works with a variety of databases, including MySQL, PostgreSQL, Elasticsearch, and Prometheus. It can also work with time series databases like InfluxDB and OpenTSDB.

### **What are metrics and visualizations in Grafana?**

In Grafana, metrics are the numerical data points that are collected over time to measure various aspects of a system’s performance. Visualizations are the graphical representations of these metrics, such as graphs, tables, and gauges.

### **What is the difference between Grafana vs Prometheus?**

Grafana and Prometheus are both popular open-source tools used for monitoring and visualization, but they serve different purposes in the monitoring stack. Here are the key differences between the two:

1. **Data Collection:** Prometheus is primarily a data collection and storage tool, whereas Grafana is a visualization and alerting tool. Prometheus collects and stores time-series data from various sources, while Grafana retrieves data from these sources and displays it in various formats.
    
2. **Querying and Analysis:** Prometheus has a powerful query language, PromQL, that allows users to query and analyze the collected data in real-time. Grafana, on the other hand, relies on data sources to provide the data and analysis capabilities.
    
3. **Visualization:** Grafana is primarily used for data visualization, providing a variety of options for displaying data in charts, graphs, and other visual formats. Prometheus, however, has limited visualization options and focuses more on data collection and analysis.
    
4. **Alerting:** Grafana provides advanced alerting capabilities, allowing users to set up alerts based on specific conditions and thresholds. Prometheus also supports alerting, but its alerting capabilities are more limited compared to Grafana.
    
5. **Ecosystem:** Prometheus has a rich ecosystem of integrations and exporters, making it a popular choice for monitoring Kubernetes clusters, while Grafana is a popular choice for monitoring and visualization of data from various sources.