---
layout: post
title:      "My Sinatra Project - CookBook"
date:       2019-07-25 09:39:45 -0400
permalink:  my_sinatra_project_-_cookbook
---


The requirements of this project were to create a website content management system using Sinatra and ActiveRecord. 

I decided to create an application that allows users a space to add, edit and manage their recipes while also having access to view other user recipes to create a crowdsourced growing cookbook of recipes. 

I started the build by considering my database and model requirements, and used tux to ensure the relationship between the recipe and user model was working effectively. 

Next my focus was on building the sign in and log in process and routes. Once I was able to authenticate a user with their name and password, I could then enable sessions and develop helper methods identify (a) whether a user was logged in and (b) who the current user was. 

Following this I worked on creating all the CRUD actions for logged in users to enable them to create, read, update, and delete their own recipes. 

Finally, once all the basic funtionaliy was working I added in rack-flash3 to generate error messages for users. I also incuded a slug for the recipe name to create cleaner urls.  


### The key learning points and takeaways

1. Use the Corneal gem to set up the basic file directory - it saves a lot of time! 

2. The usefulness of Tux - This is great gems for checking your associations and database is all functioning as expected in a safe environment. 

3. Using Binding Pry and Shotgun - Think carefully where is make sence to put in you binding.pry. Put them in route you're troubleshooting just before the point you navigate to the view or redirect in order to check variables etc. If you're using binding pry in your erb file don't forget to put <% binding.pry %>

4. Data validation - It's not sufficient to just check if users are logged in through the 'get' request. Users may be able to navigate directly to the views (particually if the routes are RESTful) and so the post actions also need to check users are logged in. 

5. Take the time to understand all the gems and how they work, there are quite a few that we can make use of in the project. Here's a quick summary that helped me keep on top of them. 

-  **Sinatra**: Obviously! 
-  **ActiveRecord** to give us access to the database mapping
-  **Sinatra-ActiveRecord** which extends sinatra  with extension methods and Rake tasks for dealing with an SQL database
-  **Rake** which is a package that lets us quickly create files and folders, and automate tasks such as database creation
-  **SQLite** which is the relational database manager 
-  **Shotgun** which allows you to see live updates to your application
-  **Pry** Troubleshooting tool
-  **Bcrypt** The gem for securing password 
-  **Tux** This gem lets you access your database and perform all CRUD operations on it through the terminal
-  **Rack-flash3** which is a simple flash hash implementation for Rack apps allowing you to easily add validation failure messages. 

6. Focus on function at a time - As there are several routes to manage it's easier to get caught up building several get requests, views and post requests at once and before which makes it more challenging if you find an error. 

7. When your coding in your Patch and Delete actions, don't forget to include the rack middleware - Rack::MethodOverride 

8. Don't forget to mount your controllers! 

### Conclusion

I really enjoyed this project; it enables you to bring together and practice all the skills through the Sinatra curriculum. I found it so satisfying building something from scratch, and it's really given me the confidence to know I can do it! 

### Next Steps
My current application is a very basic CMS with only two models (users and recipes). At a later stage I plan to come back to this to build out a separate ingredients model which would have a many to many relationship and need a join table. This would potentially allow users to search recipes by ingredient. 





