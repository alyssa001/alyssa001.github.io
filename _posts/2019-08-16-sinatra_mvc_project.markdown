---
layout: post
title:      "Sinatra MVC Project"
date:       2019-08-16 04:08:12 +0000
permalink:  sinatra_mvc_project
---


Hello world! For my Sinatra Portfolio Project I chose to create a basic site where users can share posts. My site is called CookBook so of course it is designed for foodies/cooking enthusiasts. The thought process behind this project was so complicated I don't honestly know where to begin. I spent several days planning for my project and eventually it somehow came together. A word of advice, complete the Ftwitter project before attempting the Sinatra project as it will help immensely and I wish I had done it in that order. 



My App File Structure/Description: 

Welcome to CookBook! This is a MVC Sinatra web application that allows cooking enthusiasts to post snippets of recipes or just a small post in general. This app is for cooking/food enthusiasts who wish to share their experiences and tips with others. Imagine Facebook but for cooking! 

├── Gemfile
├── Gemfile.lock
├── LICENSE.md
├── README.md
├── Rakefile
├── app
│   ├── controllers
│   │   └── application_controller.rb
│   │   └── users_controller.rb
│   │   └── cards_controller.rb
│   ├── models
│   │   ├── cards.rb
│   │   └── user.rb
│   └── views
│       ├── index.erb
│       ├── layout.erb
│       ├── tweets
│       │   ├── new.erb
│       │   ├── edit.erb
│       │   ├── show.erb
│       │   └── cards.erb
│       └── users
│           ├── signup.erb
│           └── login.erb
├── config
│   └── environment.rb
├── config.ru
├── db
│   ├── development.sqlite
│   ├── migrate
│   │   ├── 20151124191332_create_users.rb
│   │   └── 20151124191334_create_cards.rb
│   ├── schema.rb
│   └── test.sqlite

For some reason, my plan did not include a sessions_controller which I now feel should have been included, but I wasn't sure how to implement it at the time. 

I chose to use a basic HTML template for my website due to time constraints and I loaded it in layout.erb with a <%= yield %> so that I can use that page across my site and I do not need to copy and paste the same code every time I created a new .erb file. 

For my models, I added validation methods afterwards in order to make sure empty or bad data was not saved to the database and I was able to delete some extra if/else statements thanks to these validation methods. 

As far as my app structure, I kept my configure do method and get '/' method that loads the homepage in my application_controller file. I also placed my helpers in this file. I chose to have a login helper method to avoid lengthy code in my users_controller. My users_controller file contains everything related to login and signup as well as logout. It is the file that interacts with my helper methods the most. My cards_file contains all the methods and code related to CRUD. 

My database migrations were created with *rake db:create_migration NAME=file_name* to add simplicity and avoid any mistakes. 
