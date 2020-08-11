---
layout: post
title:      "JS/Rails Project - That’s So Fetch!"
date:       2020-08-11 18:27:57 +0000
permalink:  js_rails_project_-_that_s_so_fetch
---


The JS/Rails project was my first-ever full stack development! One of the most satisfying features is the ability to update the web page without reloading the page. This is functionality I wanted to incorporate in both my Sinatra and Rails projects and finally got to implement thanks to AJAX!  

![](https://media.giphy.com/media/xlYKItjhiDsY/giphy.gif)

During the brainstorming phase of my project, my daughter started asking for a puppy. We have 2 boxers that are both rescues, and I can’t justify buying a dog when there are so many out there that need/want a good forever home. So, I decided to build an application that is disguised as a dog photo/video sharing application but is designed to promote dog adoption/rescue.  

In addition to the required 3 AJAX calls to my application’s Rails API, I use an external API to fetch data on dogs available for adoption. When a user clicks on the ‘I Want One!’ button under a dog’s photo, adoptable dogs of the same breed are rendered on the page. A user can scroll through photos & information about the adoptable dogs and click on a link to learn more about how to adopt that dog.  

One of the biggest challenges I had to overcome was that the external API required not only a Client ID and Secret, but also an Access Token…which expires an hour after it’s generated. I knew how to hide a Client ID and Secret from working with OmniAuth, but nothing about utilizing the back end to handle fetching the access token and communicating it to the front end. I ended up making a custom route, a controller, and a class method to help.  

A fetch request is made to the custom endpoint, which is dispatched to the controller’s action. Inside the controller action, the class method is called. The class method makes the request with the Client ID and Secret to the external API for the Access Token and returns the Access Token. The controller action sends the Access Token to the front end to be resolved. Once the promise is resolved through chained `then()` calls, the Access Token is used in the fetch request to the external API for data on adoptable dogs.  

![](https://media.giphy.com/media/bzaEWi1Z1xzby/giphy.gif)
> 
My 2 key takeaways:  
1. Build vertically: Build out one feature at a time! Test each feature, add styles, and create seed data as you go.
2. The mantra: When WHAT event happens, I want to make WHAT request, and manipulate the DOM in WHAT way.
