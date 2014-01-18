---
layout: post
title: "Building an Ember app with Ember Appkit for Rails - Part 1"
description: ""
category: ""
tags: []
---
Last January, [Brian Carderealla](https://twitter.com/bcardarella) of
[Dockyard](http://dockyard.com), wrote up a great series of posts on building an
Ember app with RailsAPI. Since that time, Brian and others have been hard at
work building out
[EmberAppkitRails](https://github.com/dockyard/ember-appkit-rails). 

In this post, I will use Brian's series of posts as a guideline for producing a
similar Ember application, utilizing Ember Appkit for  Rails. I don't want to
speak on Brian's behalf, but I am pretty sure he would agree that Ember Appkit
for Rails is the way to go at this time for building an Ember app utilizing a
Rails backend.

Follow along with me as we build out the start of an application for tracking
books that you have read, or may want to read. Think of a simplified version of
[Goodreads](http://www.goodreads.com/). 

Let's begin:
```ruby
rails new books
```

Open up Gemfile in your editor of choice. Add the following:
```ruby
gem 'ember-appkit-rails'
```

Bootstrap ember
```ruby
rails g ember:bootstrap
```

Start your rails server
```
rails s
```

At this point, rails should start up a server on your local machine. Navigate to
```http://localhost:3000``` and you should see ```Welcome to Ember!```.

We are off and running with an Ember/Rails stack and ready to start building out
more of the books app itself, that will be covered in Part 2.
{% include JB/setup %}
