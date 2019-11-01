---
layout: post
title:      "Sinatra Portfolio Project"
date:       2019-11-01 18:24:40 +0000
permalink:  sinatra_portfolio_project
---


For my project, I decided on a web application for users to build their own recipe collections and view the recipes of other users. When I try a recipe, I find roughly 3 to 5 variations and then pull from each one. But I am terrible at saving my concoctions and when I try to make it again, I can never remember what I did previously. Thus, I selfishly decided to make a web application to keep all my concoctions for future use, with the hope of building it into a meal planning tool in the future. 

While building out and testing the project requirements, I found myself focusing on the application’s aesthetic and user experience…admittedly, more than I should. Even though this fixation took me on a few detours, and a trip or two down the rabbit hole, I found some valuable takeaways along the way.

![](https://media.giphy.com/media/swtiK9jRfE0zS/giphy.gif)

#### FLASHY STYLE

I wanted to customize the different type of flash messages displayed to the user, while keeping my code DRY. My app uses the flash keys `:error`, `:success`, `:warning`, and `:info`, and I wanted each type to have a different background and text color. I came across the Sinatra Flash gem helper method that iterates through the flash messages and renders them in styled HTML -- displaying all of the messages inside their own div element that has the same class as the flash key! Meet STYLED_FLASH! 

In your layout file, simply add the following line of code above ` <%= yield %>`

`<%= styled_flash %>`

Then add some CSS styling to style each type of message a bit differently! For example:
```
.info {
    Background :#D9EDF7;
    color: #3A87AD;
    border: 1px solid #BCE8F1;
  }
```

#### TAKE IT BACK

I wanted to add the functionality of a back button to my application, which seemed like a simple Google search away so I went for it. Alas, it was not. From my trip down the rabbit hole, I present the BACK BUTTON! 

`<button onclick="window.location.href = '<%= request.referer %>';">Back</button>`

Add some CSS styling to compliment your app! Maybe [Bulma’s button class](https://versions.bulma.io/0.7.0/documentation/elements/button/)

Cheers!

![](http://giphygifs.s3.amazonaws.com/media/PjplWH49v1FS0/giphy.gif)

