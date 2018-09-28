---
layout: post
title:      "My First CLI Project "
date:       2018-09-28 18:44:19 +0000
permalink:  my_first_cli_project
---


I've just completed my first independent coding project! Here's a brief synopsis of what I did and what I learned... 

Note - throughout all of the steps I worked through below, I constantly tested each method as I built it by calling it from my bin file and running the programme, along with pry. 

Testing every little change really helped and prevented the accumulation of multiple bugs, typos and error which would have otherwise been a nightmare to work through! 


(1) The Idea 

After a fair amount of deiberation, I decided to do a build a newsreader CLI gem to scrape TechCrunch.com. The aim of the gem was to scrape the latest 20 articles published on TechCrunch.com and allow users to select an article to read. 


(2) Where to begin

After watching and reading through all the material and setting up my gem files, I began (as Avi suggested) by thinking about the end result in terms of what I wanted user to be able to see and do. 

This meant building the CLI class first, with some initial methods to list the articles and get the user's input and display the article content, along with some hard coded dummy data (as place holders). 

Once this was working I was able to build in a couple of additional user actions 
    (a) to see the list of articles again  
		(b) to exit the programme


(3) Architecture 

I knew each article would need to be an individual object and so we definitely needed an article class with attributes for Title, Author, Time Published and Content. 

As the user would need to be able to see some form of list of all the articles, this meant I needed to both save all the intialized articles into a class array - all; and access this array via a class getter method #all. 

In addition, I needed a class to hold the scraper methods. As the article details were on the homepage, and the article content on a separate article page, two different methods were needed. 


(4) Scraping  

The scrape_from_homepage method collated from the homepage the article Title, Author and Time Published for all 20 articles in the format: 

[ {title1, time_published1, author1}, {title2, time_published2, author2}, etc.. ]

The scrape_article_content method on the other hand took the url for the individual article, and output the content for that article in the form of a long string. 


(5) Linking things up

Once I had a functioning scraper class and methods, I needed to build the necessary methods within the article class to take the output from each of these scaper methods and to:
    (a) initialize and create a new article 
		(b) assign the data to the relevant attributes for each newly created article

Next, I was able to work through the CLI class in more detail calling on the various methods built within the scraper class and the article classes to generate both the actual article list and the article content - replacing all the dummy data. 


(7) Refactoring & applying some common sense! 

Initally forgot to consider a method to clear all the articles - when testing my CLI gem I noticed each time I typed in list to generate the article list, it was growning by an extra 20 articles! This was a quick fix clear the articles each time a the scrape method was run. 

As each article url had the same structure (i.e. homepage/date_published/article-title), I thought I would be smart by building the each url from this principle. 

Whislt this worked in 80% of situations, I needed a lot of reformating of the article titles to remove puntuation, treat spaces correctly etc. After many hours of working on it, using lots of gsub's and regex, and still coming up with new errors for different articles; I built a rescue method so the programme wouldn't break down each time the article url did not work, but would instead skip over it. 

It only occured to me later that give the amount of code required to reformat and build the url, what I really should have been doing was including it article url as part of the infomation scraped! duh! 

(8) The end Result! 

! [A functioning TechCrunch newsreader CLI gem!](http://github.com/SurpreetM/tech_crunch)




