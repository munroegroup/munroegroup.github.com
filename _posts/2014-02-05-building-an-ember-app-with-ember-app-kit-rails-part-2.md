---
layout: post
title: "Building an Ember app with Ember Appkit Rails - Part 2"
description: ""
category: ""
tags: []
---
In [part
1](http://blog.munroegroupsolutions.com/2014/01/18/building-an-ember-app-with-ember-app-kit-rails-part-1/),
we got the most basic task accomplished, loading the interactive default Ember
on Rails page.

![eakr index page]({{ HOME_PATH }}/assets/images/default_page.png)

Before doing anything else, let's replace the default index page being served up by adding application and index templates to our application,

{% highlight ruby %}
  rails g ember:template application
  rails g ember:template index
{% endhighlight %}

If you refresh your homepage in the browser, you should now see an empty page.

![empty index page]({{ HOME_PATH }}/assets/images/empty.png)

Let's start moving things along and get some real work done in creating our
books application. Initially, I'm thinking each book will be represented by a
title, author, and a link to Amazon for the book. In a standard Rails project, I
might create a books resource to kick things off. With EAKR, it's a
very similar task, with a little dash of something extra, ```--ember```.

Let's go ahead and create the books resource,

{% highlight ruby %}
  rails g scaffold books title:string author:string url:string --ember
  rake db:migrate
{% endhighlight %}

Let's update the application template file, so that we see something when
navigating to the homepage.

{% highlight ruby %}
  app/templates/application.hbs

  <h1>Welcome to Books</h1>
  {% raw %}{{link-to 'Home' 'index'}}{% endraw %}
  {% raw %}{{link-to 'Books' 'books'}}{% endraw %}
  {% raw %}{{outlet}}{% endraw %}
{% endhighlight %}

Refresh your local page within the browser.

![books header]({{ HOME_PATH }}/assets/images/books_home.png)

Click the 'Books' link and add a new book.

![books one]({{ HOME_PATH }}/assets/images/book_one.png)

In Part 3, we will continue to evolve our books application.
{% include JB/setup %}
