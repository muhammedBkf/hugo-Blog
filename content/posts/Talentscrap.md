---
title: "Talentscrap"

draft: false
---

**Talentscrap** is a web scrapping script i wrote using python and Selenium to extract data from [ESI Talents](https://talents.esi.dz/scolar/public_etudiant_list) public profiles.

**Selenium** is a great tool which is primarily used to **automate** web browsing interactions for testing purposes, but is certainly not limited to just that and can be used for exemple to **scrap** data.
## Context
I was following a [course](https://www.youtube.com/playlist?list=PLroEs25KGvwzmvIxYHRhoGTz9w8LeXek0) on **databases** architectures and SQL commands.
It was a very good academic course by a professor at Stanford, it helped me getting the essential concepts, but i prefer the project based learning approach, that's why I needed some data to create a database and practice what i learned on it.

The first thing that came to my mind was ESI students data, so i went to **ESI talents** website and found that some students have their profiles public (it contains numerical values, text, images... everything I needed !), so I decided to scrap that data and use it!

![databaseScheme.png](/img/talentscrap/databaseScheme.png)

The databse scheme is quite simple : i used 2 primary keys (promo,id), with each combination of these two we get a unique student.

I'm willing to add another table to store students averages, meanwhile, you can find the source code and try it on my github.

## Conclusion
After completing this project, many ideas came to mind about automating some repetitive tasks, and making scripts that play online browser based games (like sudoku).