---
layout: post
title: "Jekyll: My Thoughts"
categories: [jekyll, webdev]
---

[Jekyll](http://jekyllrb.com/) is an interesting blog platform—it's actually just a tool that you use to generate static html files before uploading them someplace (I'm using [Github Pages](https://pages.github.com/)). No database needed, and no backend langauges required. Just static files. So far it's been a fun ride, and it sure has been a lot more fun than setting up wordpress or something similar.

### What I like about Jekyll

-	Super easy to set up.
-	Really easy to template. I copied the design I was working over and made a few changes and it was ready to go.
-	Publishing is simple with my setup, just push to github.
-	Posts can be written in my text editor of choice with markdown.

### The Basics

Getting started with jekyll is relatively easy if you are used to using the command line. Assuming you have ruby installed, you can run these four commands and get right to developing!

{% highlight bash %}
gem install jekyll
jekyll new my-awesome-site
cd my-awesome-site
jekyll serve
{% endhighlight %}

That's it! Jekyll defaults to [localhost:4000](http://localhost:4000/) for it's development server, so navigate your way there to see what it's built for you.

### Front Matter

Front matter is a list of settings that you can add to the beginning of a file. This allows you to set all kinds of things such as what layout to use, the title of the page, and more. You can add front matter like so:
{% highlight bash %}
---
layout: default
title: My awesome blog!
---
{% endhighlight %}

### Templating

The first thing you will probably want to figure out is how to set up the appearance of your blog. Jekyll uses the liquid templating system with [some added filters and tags](http://jekyllrb.com/docs/templates/). There's a lot you can do, but for a basic template all you need is the `include` jekyll tag. Basically, you have your templates, which are stored in the _layouts directory, and you have includes, which are stored in the _includes directory. Layouts are full pages, includes are snippets of pages. The interesting thing about layouts is that you can actually build on an existing layout simply by adding a reference to it in the front matter of your file. This allows you to have a default layout with your basic stuff like this:

{% highlight html %}
{% raw %}
<!DOCTYPE html>
<html lang="en">

  {% include head.html %}

  <body>

    {% include header.html %}
      
        {{ content }}

    {% include footer.html %}

  </body>

</html>
{% endraw %}
{% endhighlight %}

and then to build on that basic layout by adding page specific layouts. For instance, a basic post layout might look like:

{% highlight html %}
{% raw %}
---
layout: default
---

<main class="post">

  <header class="post-header">
    <p class="post-meta"><i>written by {{ page.author }}</i></p>
  </header>

  <article class="post-content">
    {{ content }}
  </article>

</main>
{% endraw %}
{% endhighlight %}

By adding a `{% raw %}{{ content }}{% endraw %}` tag to your layouts you are telling jekyll that if that particular layout it loaded in another file to put any additional content there. That is basic templating in a nutshell. You can then load the `post` layout in your front matter when writing a blog post and jekyll will wrap your post with all that markup.

### Blog Posts

Blog posts can be written in all kinds of formats, including markdown and textile. This gives you a lot of freedom to do what you want! To write a blog post, create a file using this format: `YEAR-MONTH-DAY-title.MARKUP`, so something like `2015-08-02-my-awesome-blog-post.markdown`. Add whatever front matter you want (layout, title, author, & category are a good start) and start typing a blog post!

### Is that all?

Well no, this only scratches the surface of what you can do with jekyll, but this _will_ give you a useable blog! Obviously you need to find hosting (I suggest [Github Pages](https://pages.github.com/)) to get it online, but it really is that simple. In the future I would like to write more about jekyll as I continue to refine and add things to this blog, so keep an eye out! Posts will most likely be a lot more focused on a specific topic and may tend to be shorter than this is.

For more information on jekyll I suggest reading through the [jekyll docs](http://jekyllrb.com/docs/home/), they give a nice overview of how to do things.