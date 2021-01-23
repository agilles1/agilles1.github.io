---
layout: post
title:      "Project 3 - orchestraNOW"
date:       2021-01-23 19:15:00 +0000
permalink:  project_3_-_orchestranow
---


orchestraNOW is a orchestra management web application providing some of the functionallity commonly found on industry standard programs such as OPAS and ArtsVision. In my work as an orchestra administrator, I interact with our relational database regularly to manage concerts and rehearsals. While I don't know the exact framework or structure of those programs, I thought this would be a great way to challenge myself to think through how it could be set up. 

The one downside to having a strong frame of reference as to how the final product should/could work and look is that it can be extremely difficult to focus on a Minimum Viable Product (MVP). This was further exacerbated with the fact that I did much more extensive wireframming than in previous projects, and therefore got bogged down at times with the look and style too early in the coding process. Live and learn! 

Here are some key orchestra terminology to help better understand my models and structure:
* **Service** - this is a term used in professional orchestras who work under a collective bargainning agreement. It refers to a rehearsal, meeting, concert, etc. Any "event" that a group of musicians (usually a minimum number defined in their CBA) are required to attend. 
* **Works** - more general term to encompass all types of musical pieces (symphonies, songs, sonatas, etc.) 
* **Composer** - person who writes music (works)
* **Epoch** - a period of time in history or a person's life, typically one marked by notable events or particular characteristics (e.g. Classical, Baroque, Romantic, 21-Century, etc.)
* **Instrumentation** - a list of the required instruments and their quantities to perform a work 

Think about any concert you go to. The group plays for hours sometimes, but do they perform every piece they have ever written? No! They put together their most popular pieces that you want to hear! We often refer to this as a "program," but in programming speak this is nothing more than a join table! In orchestraNOW, this is SerivceWorks where a Service `has many :works, through: service_works`, Works `has many :services, through: service_works`, and ServiceWork `belongs_to :service` and `belongs_to :work`. From an orchestra management perspective, this could also be expanded to include a Musicians model that can  track the orchestra personnel who perform on a particular piece or service.

This "has many through" relationship naturally lends itself to a user entered attribute via the order attribute, as the order in which a Work is on a program is extremely important! 

Another important relationship is that of a Composer and a Work. A Composer `has_many :works` and a Work `belongs_to :composer`. This relationship lends itself to being utilized as a nested resource, as there is only ever one composer (at least in this project) that a work can belong to. 

To acheive this functionality, I allow the user to create a new work for a Composer via the works show page. By selecting "create new work" from the composer's works area, the user is directed to a new form (with the use of locals) at the new_composer_work_path '/composer/:composer_id/new'. Once the form is submitted, then the create method completes the associations by utilizing the `params[:composer_id]` and `work_params`, and saves the new or edited record to the database pending it passes the validation (`validates :title, presence: true`). 

Future goals for this domain include:
* impliment user roles to allow for admins to maintain all the CRUD functionality, and musicians/performers to have read access only for the services. 
* track admin interaction (created and edit) with a service or work via a join such as UserServices 
* Expand instrumention to be an object that can be interacted with more dynamically so musicians can be assigned to services based on it. 
* Automatically generated reports
* and the list goes on...

My now wife is still waiting to see a puppy walk across the screen…come on front-end frameworks! 


