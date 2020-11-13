---
layout: post
title:      "Project 1 - MyStudio "
date:       2020-11-13 01:43:14 +0000
permalink:  project_1_-_mystudio
---


I really struggled with settling on a domain for this project. I wanted something that felt relevant and useful to others, but that wa managable and maybe pushed me just outside of my comfort zone. I started several diferrent times. Running the corneal gem to get started, I just thought. Maybe if I can just get the file structure ready the rest will just hit me! 

It didn't work. 

I was starting to feel the pressure of the deadline, so I went outside to blow the leafs. It was a beautiful fall day, and I was enjoying chasing the leave around the yard, thinking about my upcoming week and the work I had going on at Flatiron, at work, and teacing my privates students. Then it hit me! I use a continuous Google doc where I put in my students' weekly assignments. You see students are notoriously bad about "forgetting" what they were supposed to do over a week or often "lose" the little sheet of paper you scribled their assignment on, so I went digital along with teaching remote lessons, and will never go back. I can type in a lesson what I heard and leave notes about what concepts and exercises they should focus on for the coming months. But What if there was a nifty lesson assignment management application? Thus MyStudio (note the homage to the notorious social media of my youth) was born.

This project allows the teacher to create, update, read, and destroy assigments for each of their students! 

The first and maybe biggest hurdle was determining how I wanted to account for this teacher and student roles. I knew that I wanted them to have different accesses and different views, but with the ability to access the same data. So I set out to model as it happens in the real world. I, as a teacher, have many students and those students are responsible for holding onto their little pieces of paper between lessons and bringing them back the next week for us to review what they were supposed to do.

* Teachers have many Students; Students belong to a Teacher
* Students have many Assignments; Assignments belong to a Student
* Teachers have many Assignments, through Students

BUT my struggle was that both Teachers and Students are ultimately Users. I didn't want to have to write multple sign-up or login views or have these extra tables of Students and Teachers. It just seemed like a lot of works would be happenning in duplicate, so I looked for a means to destinguish these roles and still use the magic of ActiveRecord to connect them with different relationships. 

Enter the Self Join. https://guides.rubyonrails.org/association_basics.html#self-joins 

This exactly what I needed! Just like that my User class was born! 

```
class User < ActiveRecord::Base
    has_many :students, class_name: "User", foreign_key: "teacher_id"
    belongs_to :teacher, class_name: "User", required: false
    has_many :assignments, foreign_key: "student_id"
    has_many :student_assignments, through: :students, source: :assignments

    has_secure_password

    def teacher? #returns false is a User has a teacher_id
        true unless self.teacher_id && self.teacher_id > 0
    end
end
```

The hardest thing to figure out was the through relationship of Teachers to Assignments. I tried and tried to write

```
    has_many :assignments, through: :students, source: :assignments
```
 
 but it would not work! 
 
 I finally realized I was overwrititng my has_many association and therefore really confusing ActiveRecord as it was looking for these Assignements that Students owned. 
 
 I highly reccomend checking out this very cool relationship! 
 
 After that, I'm happy to say it was mostly smooth sailing. Once I had my database connections working like I planned I was able to conceptualize the various views I wanted to offer and pretty quickly get things working as I had envisioned. 
 
 Moving forward I would love to continue to grow the functionality of this application to include lession scheduling via the Google API, and potentially include some payment processing platform so teachers could accept payment from their students online! 
 
My now wife is still waiting to see a puppy walk across the screen...Maybe after Module 3?
