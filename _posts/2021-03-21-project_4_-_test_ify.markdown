---
layout: post
title:      "Project 4 - Test*ify*"
date:       2021-03-21 20:30:28 +0000
permalink:  project_4_-_test_ify
---


The saying goes "necessity is the mother of invention," and that rings true with Test*ify*. 

Since the January 2021, I have been managing the weekly scheduling of COVID-19 tests for 60+ employees. As I didn't anticipate this added responsibility to last very long, I began tracking and scheduling everything in a rather simple Excel spreadsheet. A few months later, I have ammassed hundreds of records of tests, and have been required to provide complex reports with employee test history, sending mass communications with personalized content (appointment confirmations, specific designated entrance info, etc), and finding the need to get creative with my Excel formulas and PivotTables. 

While I'm in too deep to abandon my *handy dandy* spreadsheet, I know ***there has to be a better way***! 

Test*ify* is a COVD-19 test scheduler with a Ruby on Rails API backend and Javascript frontend. 

While currently only a small component of the desired functionality I would need to utilize it in the real world, this project was the perfect opportunity to yet again apply and push my abilities as a programmer. I faced many steep learning curves along the way, but continued to challenge myself to consider the user experience as I made design decisions. 

One of my favorite challenges of this project was trying to determine how I was going to collect the updated schedule that the user creates and store it in my frontend to be able to dynamically display my available appointments on a given day. While I didn't realize it at first, I found myself contemplating a depth vs breadth scenerio for collecting new inputs. 

You see each testing block has any given number of available slots in which you would drag and drop patients into. These slots are deeply nested in a collection of <ul>, <li>, and <div> elements, some of which are blank at times. There are too many to efficiently getByElementId, and the fact that they are dynamically generated from Javascript meant the ids would change everytime, so thats not really an option. Therefore, I devised a means to drill down from the most parent element to it's farthest child, to be able to easily maintain it's association with the Javascript Appointment object. This allowed me to update my frontend "database" of appointments with the correctly associated patients, and will make for easier updating of the backend as I can then send a POST request with a collection of all Appointments (which includes their associated Patient objects) to the Appointment (my many-to-many/join table) update path.  While I am certain there are more efficient ways, to achieve the same goal I was immensely proud to do it my way!

Heres to continued refactoring and future feature builds! 




