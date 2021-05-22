---
layout: post
title:      "My Final Project"
date:       2021-05-22 14:55:13 +0000
permalink:  my_final_project
---


I can't believe I made it to this point! This final react-redux with rails API was a real challenge. 

I built a book review application where users are able to add books and add or remove reviews from them. 

I kept my idea intentionally simple so I could really spend my time throughtly understanding the interactions with the API and front end, plus the React - Redux structure. 

I stared with using rails API generator to set up my back end with controllers and models for books and their reviews. After recapping over the ruby sections in this course, this was far less daunting to do. 

It's worth spending some time here thinking about how you want your json data to be structured. In my case reviews belong to a book and so I used a serialzer to include a nested array of reviews for each book when rendering the books index. 

Moving onto the front end, the key to this form me was to understand the react-redux architecture and what each component type is meant to be doing. 

To summarise: 

- Containers: These are the primary components, and the entry point from where you call other child components. They will usually need access to map to the state to props in order to pass information to the other components to renders. 

- Actions: These are constants that contain the string value that identifies the type of action you want to dispatch. Note these will all need to also include fetch functions in order to also keep you ActiveRecord database in sync with the updates that you make to your redux store. 

- Reducers: The action creators are passed to the reducer functions which are used to manage the application’s state.  Based on the data and name of the actions being passed, the state object can be manipulated using different switch cases. 

- Components: There are the building blocks of the application, each component should have a very specific function. For example in my case I had components for the book list, book details, review list, add a new book form. 

This project was incredilby satisfying to build and was a key part in bringing together the whole course and getting a real practical hands on understanding of everything. 

Good luck everyone! 


