# SPLUNK: Exploring SPL
This project is part of Tryhackme Labs to learn and explore the basics of the Search Processing Language

## Chapter 1: Search and Reporting App Overview
Search & Reporting App is the default interface used to search and analyze the data on the Splunk Home page. It has various functionalities that assist analysts in improving the search experience.

### **Q1: In the search History, what is the 7th search query in the list? (excluding your searches from today)**
- Go to the ``Search & Reporting`` tab
- Click the ``Search History``
<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/14463556-d4e7-4c07-8120-1cdb95c74f75" />

- The 7th query is: index=windowslogs | chart count(EventCode) by Image

### **Q2: In the left field panel, which Source IP has recorded max events?**
- Still on the same ``Search History`` then I added the last search (as seen below) because it contained the source, host, index, and sourcetype, and I was expecting to find all the info I needed with the search. I also adjusted the time to “all time” so I can get full results.

<img width="1919" height="1073" alt="image" src="https://github.com/user-attachments/assets/d932bd71-8754-4f63-aa39-9030b22dfd4d" />

<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/331a8bcb-2c0e-44dd-a79e-50582a5fb4a4" />

- I observed that the left-hand panel, which lists the key fields, did not include the ip field. After expanding the More fields section, I used the search feature to locate ipaddress and sourceip. 

<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/9876c017-3aea-4a93-9ae7-0f13de2995c9" />

<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/27ab2c83-3e0d-4ac1-90a9-d70451d0e6b6" />


- From there, I identified 172.90.12.11 as the most frequently occurring source IP, with the highest number of events.



### **Q3: How many events are returned when we apply the time filter to display events on 04/15/2022 and Time from 08:05 AM to 08:06 AM?**
- Here I set the time filter as shown below

<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/7b0710c4-d79d-4749-92fc-9152e9b8ea0a" />

<img width="845" height="90" alt="image" src="https://github.com/user-attachments/assets/125f0c5e-f9a3-4bb7-99a2-aa75c607a6f3" />


## Chapter 2: Splunk Search Processing Language Overview

### **Q1: How many Events are returned when searching for Event ID 1 AND User as *James*?**
### **Q2: How many events are observed with Destination IP 172.18.39.6 AND destination Port 135?**
### **Q3: What is the Source IP with highest count returned with this Search query? Search Query: index=windowslogs  Hostname="Salena.Adam" DestinationIp="172.18.38.5"**
### **Q4: In the index windowslogs, search for all the events that contain the term cyber how many events returned?**
### **Q5: Now search for the term cyber*, how many events are returned?**


## Chapter 3: Filtering the Results in SPL
### **Q1: What is the third EventID returned against this search query? Search Query: ``index=windowslogs | table _time EventID Hostname SourceName | reverse``**
### **Q2: Use the dedup command against the Hostname field before the reverse command in the query mentioned in Question 1. What is the first username returned in the Hostname field?**

## Chapter 4: SPL - Structuring the Search Results
### **Q1: Using the Reverse command with the search ``query index=windowslogs | table _time EventID Hostname SourceName`` - what is the HostName that comes on top?**
### **Q2: What is the last EventID returned when the query in question 1 is updated with the tail command?**
### **Q3: Sort the above query against the SourceName. What is the top SourceName returned?**


## Chapter 5: Transformational Commands in SPL
### **Q1: List the top 8 Image processes using the top command -  what is the total count of the 6th Image?**
### **Q2: Using the rare command, identify the user with the least number of activities captured?**
### **Q3: Create a pie-chart using the chart command - what is the count for the conhost.exe process?**
