---
layout: NSA Codebreaker Challenge
type: project
image: img/codebreakerheader.jpg
title: "Codebreaker"
# All dates must be YYYY-MM-DD format!
date: 2022-08-26
published: false
labels:
  - Nmap
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
Here, packet logs of detected intrusions, In the logs, they were able to find SSL sessions going to the staging server and it could have been the transfer of the attackers' tools. 

