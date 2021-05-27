---
layout: post
title:      "Project 5 - Next"
date:       2021-05-27 02:10:22 +0000
permalink:  project_5_-_next
---


Long before Ariana Grande's smash hit "thank u, next" was around, those words struck fear into every orchestra musician in the audition circuit. *Next* is not the newest, hippest dating app, it's a orchestra audition management tool modeled after how I would run my own auditions while at the Pittsburgh Symphony. 

All of my projects thus far have come from ideas related to my life as a musician and orchestra administrator. While maybe a bit niche, these applications have been born out of those moments where you think "there has to be a better way" or "I wish there was an app for this!" 

*Next* allows users to manage multiple auditions simultaneously and features room auto fill functionallity, so once you get candidates in a flow of the audition the application will automatically move them through the appropriate rooms. In future version, I hope to integrate text alerts so candidates that are in the holding room would receive notfication that it's time to move to a new location, as well as a timer similar to that of a fast food drive-thru to get accurate data on how lng each candidate is onstage performing. 

One of the main challenges in this application was finding a way to best manage the state. Due to the complex associations between Auditions, Candidates, and Rooms it quickly became more effective to return the entire instance of the audition with its appropriate candidates and rooms nested within. This made for less interesting reducers, but the actions and backend still deal with a host of complexities to maintain the appropriate associations, so you don't end up with a violist from another audition in a room for a trombone audition (I think there's probably a [viola joke](http://https://www.mit.edu/~jcb/jokes/viola.html) that starts like that).

The aforementioned auto fill functionallity is by far my proudest accomplishment to date. Breaking down this real life scenrio into sound logic was a welcome challenge! While it does rely on the initial set-up of the audition to include a pre-meditated fill-order, it truly allows the audition to run its self after it begins.








