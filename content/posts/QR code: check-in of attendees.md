---
title: "QR Code: Check in of Attendees"
date: 2021-06-20
draft: false
---

# Introduction
Last week we started a strike on our campus, and every day we had to check the attendees number to make desicions according to it.  
At first people were siging on paper lists, which we have to print in advance, so they have to find theirs names on the list then sign, with this method we took around 1 hour to complete the check-in process.
And due to covid restrictions we had to avoid people regrouping on the check-in table. That's why we had to find a better solution to this problem.  
An idea has come to my [friend](https://github.com/imadbourouche)'s mind and proposed to make a digital solution using a qr code scanning app, we immidiatly discussed the feasibility of the solution and start coding.  
- We first had to make a database with all the **students emails**, we searched a bit then found that available on our campus messaging service.  
- Then we had to generate a **unique QRcode** for each student and make a script to send it to it's owner.  
- Make the app that **scans** the QRcode and validate the attendance.
- Generates a **sheet** with the attendees list and the time in which they arrived.

This took us a weekend to implement, and we had no previous knowledge about some of the technologies we used like openCV.

After that we could even add a **dashboard**.
![stats.png](/img/qrcode/stats.png)  

|input|output|         
|----------------|-------------------------------|
| ![blender](/img/qrcode/1cp.png) |![blenderAscii](/img/qrcode/2cp.png) |

## Conclusion

After introducing this solution the check-in was speed up by 6 times, it took 10 mins instead of 1hour to complete it.  
The strike lasted 4 weeks, so this solution helped us saving a lot of time and money.