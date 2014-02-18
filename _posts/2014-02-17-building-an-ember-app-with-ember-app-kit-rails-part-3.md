---
layout: post
title: "Building an Ember app with Ember Appkit Rails - Part 3"
description: ""
category: ""
tags: []
---
In [part2](http://blog.munroegroupsolutions.com/2014/02/05/building-an-ember-app-with-ember-app-kit-rails-part-2/), we added a books resource to our books application and showed that the resource was working by typing in the title, author and Amazon URL for a sample book.

You can find the source code for this app at [Github](https://github.com/mikepmunroe/books-EAKR).

Before we move any further in building out our app, let's add some
style using a CSS framework. Most apps built for show and tell type purposes
these days are typically built with [bootstrap](http://getbootstrap.com/), but I recently saw a blog post on the use of
[Foundation](http://foundation.zurb.com/), so let's give that a try.

Open up your Gemfile and the following,
{% highlight ruby %}
  gem 'foundation-rails'
{% endhighlight %}

Complete the following steps,
{% highlight ruby %}
  bundle
  rails g foundation:install
{% endhighlight %}

During the ```rails g foundation:install``` step, you will probably be prompted
to overwrite your ```application.html.erb file```. Allow the overwrite to occur. After the foundation install completes, let's change the default title back to ```Books```.

Change,
{% highlight html %}
  <title>
    <%= content_for?(:title) ? yield(:title) : "foundation-rails" %>
  </title>
{% endhighlight %}
to
{% highlight html %}
  <title>
    <%= content_for?(:title) ? yield(:title) : "books" %>
  </title>
{% endhighlight %}
Restart your rails server. Your page should look similar to,

![foudation index page]({{ HOME_PATH }}/assets/images/foudation.png)

Our home page is a bit empty. Let's get some books listed on the home page by setting the default route to automatically redirect to the books resource index page.

Add the following code to ```app/config/router.js.es6```,
{% highlight javascript %}
  App.IndexRoute = Ember.Route.extend({
    beforeModel: function() {
      this.transitionTo('books');
    }
  });
{% endhighlight %}

Your full ```app/config/router.js.es6``` should match the following,
{% highlight javascript %}
  var Router = Ember.Router.extend({
  // Uncomment to change Ember's router to use the
  // HTML5 History API
  // Please note that not all browsers support this!
  // You will also need to uncomment the greedy route matcher
  // in config/routes.rb

  // location: 'history'
  });

  Router.map(function() {
    this.resource('books', function() {
      this.route('new');
      this.route('show', {path: ':book_id'});
      this.route('edit', {path: ':book_id/edit'});
    });
  });

  App.IndexRoute = Ember.Route.extend({
    beforeModel: function() {
      this.transitionTo('books');
    }
  });

  export default Router;
{% endhighlight %}

The homepage should now look similar to,

![books index page]({{ HOME_PATH }}/assets/images/books_index.png)

In part 4, we will adjust the UI to put some polish on the look and feel of our app.
{% include JB/setup %}
