---
layout: post
title:      "Javascript Project"
date:       2020-10-23 16:57:20 +0000
permalink:  javascript_project
---

### Rails backend API

This has to be one of the most challenging projects for me so far, but I feel so accomplished having finally built it. I decided to focus on a simple app with just one belongs to and has many relationship, with the intention that I would be able to expand from here. 

My project idea is a virtual menu, with food items belonging to heading (e.g. Appetizers)/ 

In order to get started with building my single page app I needed a Rails API backend. I used the following to get started. 

$ rails new my_api --api

Next I used rails resource generators to set up the models, controllers, views, and migrations for my two resources. I seeded database with some initial data. 

I then used the fast_jsonapi to create model serializers. If you're looking to extract out the customization of the JSON data from the controller, this provides a quicker alternative to manually extracting a service class. 

Next I added the route actions in the each of the controllers rendering JSON via the model serializer. 

Once I'd done all this I was able to run the rails server and see the format of my JSON data by going to Going to localhost:3000/headings

### Javascript Front End 

For me this was the most challenging part, rather than talk chronilogically through all my steps, I'll just highlight me key learning points: 

1. Take your time to understand your front-end struture 
It needs to be object orientated, and so you should expect to have classes that allign to your backend models, but also you can create an APIConnector class to hold all your fetch methods for both pulling and posting data.

2. Use console.log(object) to see the information passed back from the server in your post requests using fetch()
This really helped me understand what was happening, and it also allowed me to create my javascript objects from it.  

3. Start simple and focus on one thing at a time
Everytime I refered back to the technical requirements it completely overwhelmed me. As soon as I just thought about the one thing I wanted to get working it really helped. For me once I fetched the JSON data the rails API and was able to manipulate it using javascript and generate a static html page with no other functionality, I suddenly felt like I was understanding things a lot more.

4. Validations
This took me a while to figure out where they should sit and I wasted a lot of time building check points with custom alterts in my javascript methods to ensure that form data was populated correctly. I finally concluded that the validations should be within the rails API models themselves as then the validation would occur before saving the record to the activerecord database. Rails also provide an array of strings or the error message that you can then use generate your alerts in your front end. 

5. Validations - customizing messages
Some of the standardized ruby error messages might not be great from a user persective as they refer to the attribute names. Within .../config/locales/en.yml you can rename these attributes for use in the error messages: 

en:
  activerecord:
    models:
    attributes:
      heading:
        name: "Heading"
      food_item:
        name: "Food Item"

Here I am saying to refer to the heading model, name attribute as "Heading" in the error handling message and for the food_item model's name attribute to be referred to as "Food Item" 


Overall, I really enjoyed the success of this completing this project. Looking back to where I starting building, I can't even believe how far I've come! 
