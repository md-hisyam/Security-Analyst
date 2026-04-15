# SPLUNK: Exploring SPL
This project is part of Tryhackme Labs to learn and explore the Splunk's Search Processing Language

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
<img width="1919" height="850" alt="image" src="https://github.com/user-attachments/assets/2c59b3bd-309d-4a9e-af5d-f40bf4f08f60" />

### **Q2: How many events are observed with Destination IP 172.18.39.6 AND destination Port 135?**
<img width="1919" height="868" alt="image" src="https://github.com/user-attachments/assets/02d266fb-20b3-4653-86d6-9028e0255ab8" />

### **Q3: What is the Source IP with highest count returned with this Search query? Search Query: index=windowslogs  Hostname="Salena.Adam" DestinationIp="172.18.38.5"**
<img width="1919" height="869" alt="image" src="https://github.com/user-attachments/assets/68815861-f964-4d4e-ba2f-1b1e953165b0" />

### **Q4: In the index windowslogs, search for all the events that contain the term cyber how many events returned?**
<img width="1914" height="868" alt="image" src="https://github.com/user-attachments/assets/be125ea7-66f7-4484-8a10-11a1bc08da4d" />

### **Q5: Now search for the term cyber*, how many events are returned?**
<img width="1919" height="866" alt="image" src="https://github.com/user-attachments/assets/3ef12599-76d8-4844-aa1e-c9198ebf26e4" />


## Chapter 3: Filtering the Results in SPL
### **Q1: Use the ``fields`` command to highlight ``Domain``, ``SourceProcessId``, and ``TargetProcessId``. Which SourceProcessId has the highest value?**
<img width="1919" height="1063" alt="image" src="https://github.com/user-attachments/assets/db823811-9b68-41f0-a9c3-b320122a714d" />

### **Q2: Try out this query ``index=windowslogs | regex TargetObject="Manager$"``. Which ``TargetObject`` field value contains the highest number of results?**
<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/ba0eb05c-ed91-4b12-8c15-42a260370bbe" />


## Chapter 4: SPL - Structuring the Search Results
### **Q1: Build a table that highlights the ``EventID``, ``AccountName``, and ``AccountType`` fields. Which ``AccountName`` appears first in your results?**
<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/6045de81-63b6-45e6-9be1-47a3d7f0705c" />

### **Q2: Append the above query to include the ``reverse`` command. Which ``EventID`` appears first?**
<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/b2a874e1-6e21-4a4e-95e6-6637c8f41bf2" />

### **Q3: Use the query below to build a timeline of events. What password was given to the user ``A1berto``?**
```
index=windowslogs EventID=1
| table _time ParentProcessId ProcessId ParentCommandLine CommandLine
| reverse
```
<img width="1919" height="1079" alt="Screenshot 2026-04-15 141124" src="https://github.com/user-attachments/assets/3e6a183e-ebbc-43f0-9c80-116964af1f79" />


## Chapter 5: Transformational Commands in SPL

Transforming commands allow us to change raw event data into useful summaries, statistics, and visualizations. Instead of viewing every individual log, they help analysts aggregate, count, and analyze patterns across many events. Searches that utilize transforming commands are referred to as transforming searches in Splunk.

### **Q1: Use the ``top`` command to query the ``Image`` field. Which ``Image`` field value has the most occurrences?**
<img width="1919" height="866" alt="image" src="https://github.com/user-attachments/assets/bd92a836-f260-40c7-86fa-70648a90bb3f" />

### **Q2: Try out the ``iplocation`` command with the ``SourceIp`` field. Which ``Region`` do the IP addresses in your events originate from?**
<img width="1919" height="870" alt="image" src="https://github.com/user-attachments/assets/e5af86e6-f240-4920-9a2b-337141b92817" />

### **Q3: Try out this ``lookup query``. Which ``Image`` field value has the highest ``RiskScore``?**
```
index=windowslogs
| lookup image_riskscore Image OUTPUT RiskScore
| stats count by Image RiskScore
| sort - RiskScore
```
<img width="1919" height="868" alt="image" src="https://github.com/user-attachments/assets/1e6bd1c4-c7c0-4eb3-93fb-f54c80e8af5d" />



## Chapter 6: Anomaly Detection 

If I’m investigating a dataset with lots of events (like VPN logins), I need a way to quickly spot outliers—things that don’t fit the normal pattern. For example, if I have around 2,000 VPN login events with fields like time, username, source IP, and source country, and basic field statistics don’t reveal anything unusual, I would shift my approach.

From my point of view, I’d start grouping and counting values to understand what “normal” looks like. I’d likely use something like top or stats count by source_country to see which countries appear most often. Once I know the common countries, I can look for the rare ones—those with very low counts—which could indicate unexpected or suspicious logins.

I might also filter out the known, expected countries and focus only on the uncommon ones. Another approach I’d take is correlating users with countries (e.g., stats count by username, source_country) to see if a specific user suddenly logs in from a country they don’t عادة use.

In short, instead of relying on default statistics, I’d define what “normal” looks like in the data and then actively search for deviations from that baseline.



