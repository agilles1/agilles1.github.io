---
layout: post
title:      "Project 1 - Pittsburgh Cultural District Events CLI"
date:       2020-09-17 13:13:12 +0000
permalink:  project_1_-_pittsburgh_cultural_district_events_cli
---

One of the hardest parts of starting this project for me was deciding what it was going to be. I wanted it to feel usefull and relevant to my life. After much refelection, I thought about using my own company's public facing website as the source of information. I began building my app and got it working with some "dummy" data. I was extatic! Then the scraping began. I devised a plan to scrape the events' names, dates, and ticketing url. It was all going well, I thought! But then the 405 errors began....

It didn't make sense! One minute I could scrape all the info I needed, then I would try to scrape again or scrape a second page and boom ERROR! I looked online for as many options as I could to troubleshoot or work around, and I could not get it to work. After much frustration, I reached out to the web developer and she was so gracious to let me know that it would probably never work. Womp womp. The security settings on the site throttled requests and specifically blocks bot requests. So now what?!

I could either change my whole project or try to find another site. neither felt like awesome options. Luckily I stumbled on the Cultural District's site. They included all of the same events from my work, and more from other presenters in the city! It was an even better, more robust option! AND they offered their events informatin in a RSS format making for much easier scraping. 

I was fortunate to have a lot of free time early on in this module to work ahead, so I came to the CLI project much earlier than my cohort. After getting the basic framework working with real, scraped information, I began this vicious cycle of "oh I should add!" This was extremely fun, frustrating, and ultimately satisfying. I began to expand to include more object relationships (adding unique Venue and Presenter Classes) and even ended up trying to mimic object permanence with a User Class (now you can login to the browser, and reference your browsing history).

All in all it was an extremely satisfying project, and I look forward to the next one! 

My fiance keeps asking me, "can you make a puppy walk across the screen yet?" Maybe after Module 2?
