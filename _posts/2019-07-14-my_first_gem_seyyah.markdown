---
layout: post
title:      "My First Gem ~ Seyyah "
date:       2019-07-14 16:33:31 +0000
permalink:  my_first_gem_seyyah
---


**Summary**
After one month as a FlatIron student, I came to the moment of creating my first project, a CLI Ruby Gem. For this project, I chose to create a gem that would scrape information from LonelyPlanet. I named my gem 'Seyyah' as it actually means 'Traveler' in Turkish. The idea was to have my CLI provide a user with a list of regions around the world and the user would make a selection from those regions. After a user selects a region, they will be provided with a description of the region and the top 10 most popular countries in that region and asked to select a country to learn more about it. Once a country is selected, the user will see a detailed summary of that country as well as the top cities in that country. 

**Planning**
Most of my original planning and notes evolved as the project progressed, especially when I inspected the HTML elements of the web page I wanted to scrape. Originally, I had planned for the gem to go several levels deep, scraping all the available countries in that region, not just the most popular destinations, but as that would require my program to scrape over 50 web pages, I discarded that idea and stuck with only the most popular destinations. 

**The Beginning**
I chose to use a local environment for my gem and I created my gem with bundler from the terminal. I used Visual Studio Code for my program as it is free and has many useful extensions available for download. I originally started coding my classes and left the CLI interface for last. I started with scraping the web pages and because I wanted to present the regions and countries in an ordered list, I used repl.it to check the output of the functions I wrote to scrape the pages. I decided not to include modules in my program and stuck with classes that called on each other. The original gem before refactoring ended up being too long and I decided to finish writing it before making the program more concise and neat. Since I waited until the end to refactor the program, I had a very clear idea of what items relied on each other and I was able to work more effectively. 

The general set-up for my program was as follows: 
***Seyyah ***
    *--> Regions of the World
        --> Region Description & Top 10 Countries by Region 
            --> Country Description & Top 10 Cities by Country *
						
**Creation**
I chose to create my files as follows: 
* cli.rb --> contains my CLI interface
* regions.rb --> scrapes the initial webpage and returns the countries
* countries.rb --> scrapes the secondary webpages for the countries
* destination.rb --> scrapes the country webpage and returns destinations


I was also lucky enough that the website I chose to scrape had the same html tags for both the regions pages and the country pages so it shortened my workload and made it easier to share methods between classes and in my interface as well. Because the web page that I was using had grouped together the top countries and cities, I had to use enumerators in my code. I couldn't find a way to get the .each_with_index to work, so I had to come up with another way to solve this.  The following code was my solution: 
```
def self.regions(url)
        html = open(url)
        doc = Nokogiri::HTML(html)
        counter = 0

        doc.css("#destinations-menu-desktop .Submenu__list--3MiRl .Item__container--_wmB6").each do |n|
            regg = n.content
            counter += 1
            puts "#{counter}. #{regg}" 
        end
				
				#The code above outputs: 
				#1. Country
				#2. Country
```

**Conclusion**
I am still working on refactoring my code into something more elegant and concise and I plan to include a few more levels of scraping to continue practicing with Ruby. Eventually I hope to extend my program to include all the countries in the regions and to include the top tourist destinations and their cost as well. I enjoyed my first project very much and now I'm just waiting for the project assessment to get some feedback on how I can improve my code. 
