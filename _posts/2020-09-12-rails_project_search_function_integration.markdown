---
layout: post
title:      "Rails Project Search Function Integration"
date:       2020-09-12 17:47:02 +0000
permalink:  rails_project_search_function_integration
---


For the live coding challenge of my Rails project review, I needed to add a search feature to one of my index pages. 

My project is a basic game reviewer. Users can read and write reviews from other users of existing games. The games index page contains all of the games in the database. There, users can rate any of the games on the list. The page, now, also allows users to search through all of the games in the database.

When given the challenge, I knew I needed to lay out my functionality structure:

* Make a search form (using form_tag since we aren't actually manipulating any models)
* Set path (used rake routes to get proper route) for form_tag and method to "get" since we aren't posting to the    database
* Permit "search" field in games_params
* Create search class method for querying
* Set class method to return all games if user not using search. If using search, return the game searched for if found. If not found, render view as normal (return all games)
* Set index action in the controller as @games to return the "search" class method

After laying out my structure, it was just a matter of taking my theory and making it reality. I, first, got the search bar (form) to render on the page. Then it was time for functionality. I permitted the search field in the game_params method. From there, I created the class method "self.search" with a "search" argument so we'd be able to use a param for that class method when we call it in our controller. In our class method, we need a nested if statement. If we use the search feature, try to find the game by the game title using the "find_by" method. If not using the search feature, ("else") simply return all games as we normally would. But if we find that game, return it using the where method and the id for that specific game. If we can't find the game, we render the index page as we normally would. 

After fixing a few spelling errors and adding/removing colons and other punctiation, my search feature works and it's awesome!
