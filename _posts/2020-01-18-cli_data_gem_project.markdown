---
layout: post
title:      "CLI Data Gem Project"
date:       2020-01-18 23:10:15 -0500
permalink:  cli_data_gem_project
---


This project was the first real test in the curriculum. From the very beginning, I could tell that there were going to be several major roadblocks. For my CLI Gem, I opted to go with something simple so that I could focus on the process of building a gem and making sure that my code was clear, concise, and as simple as possible. To that end, I decided to make a gem that simply pulled data from two websites to tell you what weird holidays it is (today happens to be National Thesaurus Day and Maintenance Day).  As I suspected, even with such a tame end goal, there were several difficulties that I had to overcome before this project would be complete.

The first major challenge that I encountered was simply setting up my environment. Having never constructed a Ruby gem before, it was definitely a process to learn how to set up all of the proper directories and files, and getting my load dependencies in order took some time as well. Ultimately, the walkthrough that Flatiron recommends was very helpful to someone like me who was coming into this with next to no experience. I eventually decided to set up my environment in ./lib/weird_holidays.rb file, and then simply require that one when the gem is first loaded.
![My Environment:](https://imgur.com/Cq0EjDJ)

Once I had my environment completely set up and ready to go, it was time to begin constructing my gem. Following the advice given in the walkthrough, I began by simply writing out pseudocode to explain to myself what I wanted each part of my program to do. I liked the way that they put it when they said to "write the code that you wish you had." I found this to be a very helpful rule. Just writing out code that worked with methods that I hadn't constructed yet made it easier to see what it was that I needed to work on next. 

The next big challenge I had arose when it came to the actual scraping. Both of the websites that I wanted to use did not have the second layer of data on the same page as the data that I was going to be scraping originally. Because of this, I needed to be able to open an embedded link on each page and then scrape data from the webpages that those links opened. At first, I just hacked the links together by splicing the names of the holidays that I was scraping from the first page so that I could get my program to be fully functional for testing purposes. However, there were two huge issues with this. The first was that it would break any time that there was punctuation in the name of the holiday, for instance if it was formatted as Martin Luther King Jr.'s Birthday, but it was also just sloppy code. It was not completely functional, and it looked horrific, so I had to fix it. 

I spent quite some time trying to figure this one out. None of the resources that I could find online talked about scraping href values from link elements. Eventually, I was able to find a solution. Instead of trying to grab that particular value from the link element, I converted the entire thing to an array. Unfortunately, this included things like the title and a dozen other little values that I didn't care about at all. To fix this, I had to use the .map functionality that arrays carry in Ruby. I used the .map function to go over the array and check to see if each element was labeled "href," and then return it in the new array if it was. By doing this, I was able to grab just the url and then go from there.
![My .map Logic:](https://imgur.com/FBuxkHz)

The final big challenge of this project came at the very end when it was time for me to publish my gem. I kept running into a NameError where the main class in my cli file was not loading properly. Everything functioned when I ran the program locally, but as soon as I tried to publish it things were starting to break. Pretty early on, I identified this as an issue with loading my dependencies. Unfortunately, this was another problem where it was difficult to find any resources online that were specifically about it. Eventually, I started checking other gems to look at their gemspecs and see if they had anything that was different than what I had. What I found that ultimately fixed the problem was this:
![My Gemspec Fix:](https://imgur.com/MWYlFPmhttp://)

All in all, I definitely learned a lot while working on this project. It gave me a lot of opportunity to problem solve and I grew a lot more familiar with scraping using Nokogiri. I've already learned a lot during my time with Flatiron, and I look forward to growing my skillset even more over the coming months. 
