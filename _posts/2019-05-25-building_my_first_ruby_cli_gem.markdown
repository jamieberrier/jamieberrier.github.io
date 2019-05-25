---
layout: post
title:      "Building My First Ruby CLI Gem"
date:       2019-05-25 20:17:48 +0000
permalink:  building_my_first_ruby_cli_gem
---

My first blog post about my first Ruby CLI gem…Here goes nothing!

The inspiration for the website I used for this project came to me while my daughter was attending a spring break camp at San Diego’s Balboa Park. For 5 days, I had the luxury of doing my schoolwork under the warm Southern California sunshine while she was in camp. I got my coding on at the tucked away sculpture garden or on the grassy lawn next to the Lily Pond full of ducks, turtles, koi fish, and lily pads surrounded by beautiful plants, trees, and flowers with music flowing through in the air….courtesy of whichever acoustic guitarist happened to be posted up on the bridge over the pond. 

When I needed a break, I wandered the grounds and gardens or strolled through a free museum….basically discovering all the different events happening at the park. It was during one of these breaks that I had my ‘AH-HA!’ moment and decided to scrape the Balboa Park website of all of its diverse happenings. On the website I found a section which featured current events called, What’s Happening Today. Perfect! I’ll give the user the info for each of the featured events, ask them to choose an event, and then display the details of that event for them.

After designing the interface, planning the gem, and feeling inspired….I was ready to sink my teeth in. After building the executable file, the environment file, and a working CLI that collaborated with the hardcoded scraper and event classes I was ready to use those teeth, err, I mean, a fine-toothed saw, for scraping to make things real. I wanted to pull the welcome header and message for the CLI to use to greet the user…easy peasy lemon squeezy. Now on to the meat and potatoes, the information for the featured events. However, after much trial and error, googling, and head banging, the text I wanted to use was not appearing in any of my scraping attempts. Welp, I learned that the content I wanted is being loaded by JavaScript which means it's not there before Nokogiri gets to it. I had 2 options….1) I could stick with scraping that data by using an alternative scraper gem called Watir or 2) stick with Nokogiri by using a different section of the site. I chose to see what was behind door #2.

The bad news, I had to start all over. The good news, I had just basically built a CLI gem so things should move fairly quickly. Luckily, I was right, and things went smoothly the second time around with scraping the ‘Itinerary Ideas’ section of the website. The challenges I faced now were in the details. There are 9 itineraries to choose from, each with its own webpage that displays a summary, 11-32 attractions with detailed (and sometimes lengthy) descriptions, and a link to the attraction’s site (if it had one). I had to do some selective scraping for variances in the itinerary pages. For example, the ‘Explorer’ itinerary has an image hyperlink in its summary. 

Also, the lines of text were wrapping in the middle of words, which made the info not only unpleasant to look at but also difficult to read…especially the ‘Birds of Balboa Park’ itinerary which had 3 paragraphs of text for each of the 32 birds. After another round of much trial and error, googling, and head banging, I came across the ‘strings’ gem. Strings is a set of useful functions, such as: fold, truncate, and wrap, for transforming strings. The wrap function, aka my new best friend, takes in 2 arguments: text and wrap_at, to wrap the text into lines no longer than the wrap_at argument length…i.e. Strings.wrap(text, 30). Hats off to Piotr Murach for creating this gem of a gem! Once it no longer hurt my eyes to look at my CLI, I further improved its aesthetic with the ‘colorize’ gem. 

While I may or may not have given myself a mild concussion during this process, I did come away with a much-improved sense of confidence in coding. 

Now on to publishing my gem…here goes nothing!
