---
layout: post
title: "Building an Ember app with Ember Appkit Rails - Part 4 - Conclusion"
description: ""
category: ""
tags: []
---
This is the conclusion to a 4 part series on creating a simple Ember application using [Ember Appkit Rails](https://github.com/dockyard/ember-appkit-rails)

In [part3](http://blog.munroegroupsolutions.com/2014/02/17/building-an-ember-app-with-ember-app-kit-rails-part-3/), we set our application home page to render the books' resource index.

To finish off our app, let's clean up some of UI for a more polished look.

**Remove headers from some of our templates:**

app/templates/application.hbs
{% highlight javascript %}
  {% raw %}{{outlet}}{% endraw %}
{% endhighlight %}

app/templates/books.hbs
{% highlight javascript %}
  {% raw %}{{outlet}}{% endraw %}
{% endhighlight %}

app/templates/books/index.hbs
{% highlight html %}
  <p>{% raw %}{{link-to 'New book' 'books.new'}}{% endraw %}</p>

  <table>
    <tr>
      <th>id</th>
      <th>Title</th>
      <th>Author</th>
      <th>Url</th>
    </tr>
    {% raw %}{{#each}}{% endraw %}
      <tr>
        <td>{% raw %}{{link-to id 'books.show' this}}{% endraw %}</td>
        <td>{% raw %}{{title}}{% endraw %}</td>
        <td>{% raw %}{{author}}{% endraw %}</td>
        <td>{% raw %}{{url}}{% endraw %}</td>
      </tr>
    {{/each}}
  </table>
{% endhighlight %}

**Add a navigation bar:**

app/templates/application.hbs
{% highlight html %}
  <nav class="top-bar" data-topbar>
    <ul class="title-area">
      <li class="name">
        <h1><a href="/">Books</a></h1>
      </li>
    </ul>

    <section class="top-bar-section">
      <ul class="right">
        <li class="active">
          {% raw %}{{#link-to 'books.new' classNames="button"}}Add New Book{{/link-to}}{% endraw %}
        </li>
      </ul>
    </section>
  </nav>

{{outlet}}
{% endhighlight %}

**Update UI for crud actions:**

app/templates/books/form.hbs
{% highlight html %}
  <form>
    <div class="row">
      <div class="large-4 columns">
          {% raw %}{{input value=title placeholder="Enter a Title"}}{% endraw %}
      </div>
    </div>
    <div class="row">
      <div class="large-4 columns">
          {% raw %}{{input value=author placeholder="Enter an Author Name"}}{% endraw %}
      </div>
    </div>
    <div class="row">
      <div class="large-4 columns">
          {% raw %}{{input value=url placeholder="Enter an URL"}}{% endraw %}
      </div>
    </div>
    <div class="row">
      <div class="large-4 columns">
        <button type="submit" class="tiny button"  {% raw %}{{action save this}}{% endraw %}>
          Save
        </button>
        <button type="submit" class="tiny button"  {% raw %}{{action cancel this}}{% endraw %}>
          Cancel
        </button>
      </div>
    </div>
  </form>
{% endhighlight %}

app/templates/books/index.hbs
{% highlight html %}
  <div class="row">
  <table>
    <tr>
      <th>Title</th>
      <th>Author</th>
    </tr>
    {% raw %}{{#each}}{% endraw %}
      <tr>
        <td><a target="_blank" href="{{unbound url}}">{% raw %}{{title}}{% endraw %}</a></td>
        <td>{% raw %}{{author}}{% endraw %}</td>
      </tr>
    {% raw %}{{/each}}{% endraw %}
  </table>
</div>
{% endhighlight %}

app/templates/books/new.hbs
{% highlight html %}
  <div class="row">
    <h3>Add New Book</h3>
  </div>

  {% raw %}{{partial 'books/form'}}{% endraw %}
{% endhighlight %}

app/templates/books/show.hbs
{% highlight html %}
  <div class="row">
    <ul>
      <li>Title: {% raw %}{{title}} {{link-to 'Edit' 'books.edit' this}}{% endraw %}</li>
      <li>Author: {% raw %}{{author}} {{link-to 'Edit' 'books.edit' this}}{% endraw %}</li>
      <li>Url: {% raw %}{{url}} {{link-to 'Edit' 'books.edit' this}}{% endraw %}</li>
    </ul>
  </div>

  <div class="row">
    <button class="tiny button" {% raw %}{{action destroyRecord this}}{% endraw %}>Delete</button>
  </div>
{% endhighlight %}

Add the following file:

app/assets/stylesheets/index.css
{% highlight css %}
  .top-bar {
    padding: 0px 115px;
  }

  .row h3 {
    margin-left: 15px;
  }

  .row table {
    width: 63em;
  }

  .row table th {
    text-align: left;
  }
{% endhighlight %}

Following those changes, the application loaded in your browser should look similar to this screenshot:

![final index page]({{ HOME_PATH }}/assets/images/final.png)

The books application that we ended with is very simple. There are a few things that the application could benefit from that might be good tasks to take on independently to level up your Ember knowledge. Some things that the app could probably benefit from include:
  * authentication
  * paging
  * form validation


Good luck in your journey learning Ember. Be sure to come back to see posts on other Ember topics.

{% include JB/setup %}