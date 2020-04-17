---
layout: post
title:      "My Rails Portforlio Project "
date:       2020-04-17 19:23:59 +0000
permalink:  my_rails_portforlio_project
---


This was so much fun to build, and super satisfying. Rails generators and helper mean that you can get started and have a functioning application in no time. 

The main takeaways for me: 


### Spend your time planning before your build
Think through your models and how they should be associated to one another, does a belong_to has_many relationship suffice or do you need to consider join models for other associations. 

Thinking through this initally will save lots of time setting up migrations and having to make changes and rollback databases. 


### Understand what the helpers and generators really do
Rails does seem like magic when your using their helpers and generators but as soon as something doesn't work as expected, unless you fully understand what they do it can become incredibly difficult to trouble shoot. 

For example I spend far too long misunderstading the difference between link_to and button_to and assuming it was simply a formatting difference. However they not as simply interchangable like that! 

-  button_to uses the :POST method by default
- link_to uses the :GET method by default

Therefore if you want a link to send  a :POST method to one of your routes, you need to also pass the correct method otherwise you will get a routing error. 

**Example** 
<% = link_to "Click here to submit post.", posts_url, method: :post %> 


### Check you routes  
Try not to be lazy and just use resources :products but be clear about what routes exactly you need, i.e. resources :products, only: [:index, :show]


### Enjoy yourself! 
This was one of the most intimidating projects so far as rather than have a simple application with a single objective, the requirements for this one included a whole suite of things to consider! 

Looking at the end result now, I simply can't believe how far I've come and what I've been able to build. 

Thanks Flatiron! 


