---
layout: NSA Codebreaker Challenge
type: project
image: img/codebreakerheader.jpg
title: "Codebreaker"
# All dates must be YYYY-MM-DD format!
date: 2022-08-26
published: false
labels:
  - GitHub
  - -Wireshark
summary: "An NSA Challenge to find a Hacker using various tools"
---


<img class="img-fluid" src="../img/codebreakerheader.jpg">

Codebreaker is a challenge given by the NSA that consists of various tasks. The goal is to find the hacker who breached security measures and stole private data. I will explain each task and what I did to complete the challenge.

<h1> Task A1: Initial Access </h1>
In this task, we are given the VPN log to look through. The VPN log consists of the server logs for the week it took place. I had to look for anything suspicious and out of the ordinary. 
Since each employee can only log in once, I looked at multiple connections at the same time.

<h1> Task A2: Identifying the Attacker </h1>
Here, packet logs of detected intrusions, In the logs, they were able to find SSL sessions going to the staging server and it could have been the transfer of the attackers' tools. In this task, I used a tool called 'Wireshark' to decrypt SSL sessions, and find their tools, and extract them. Then I had to open the file in the hex editor to remove the headers and extract the username of the owner of the file. 

<h1> Task B1: Information Gathering </h1>
In this task, we are given the attacker's demands in exchange for the stolen files. The attackers left a website with their demands and an address to send 'RansomCoin'(bitcoin). To finish this task, we have to look at the network traffic built into my browser such as the web dev tools, to find any other ransomware websites. and H! and Behold! We find external requests to other sites the attackers used.

<h1> Task B2: Getting Deeper </h1>
In this task, we have to analyze the backend website that we found in B1. I again used the web dev tools to analyze the website, upon analyzing I found a '.git' directory. To get the directory, I had to use a tool called 'GetTools' to extract the directory by cloning it. Upon cloning the directory, we had to look at the server files to see if there was anything left behind. I had to carefully look at the codes in the server files to find clues as to figure out how each file connects to one another. This part was really tricky because I had to follow the functions and their parameters which returns another parameter that leads to pathkeys. Upon, finding the final return to the path key, I reused to backend webpage and added in the path key which led me to the login URL that the attackers used. 

<h1> End of the Project </h1>
Unfortunately, we never got to finish the project because the other task required more experience and was a lot more complicated. So, our Professor only made us do the first four tasks. But, it was fun. I learned a lot of useful tools and experienced the process of cybersecurity.  
