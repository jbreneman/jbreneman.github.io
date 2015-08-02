---
layout: post
title: "Jekyll: My Thoughts"
categories: [jekyll, webdev]
---

[Jekyll](http://jekyllrb.com/) is an interesting blog platform—it's actually just a tool that you use to generate html files before uploading them someplace (I'm using [Github Pages](https://pages.github.com/)). No database needed, and no backend langauges required. Just static files. So far it's been a fun ride, and it sure has been a lot more fun than setting up wordpress or something similar.

### What I like about Jekyll

-	Super easy to set up.
-	Really easy to template. I copied the design I was working over and made a few changes and it was ready to go.
-	Publishing is simple with my setup, just push to github.
-	Posts can be written in my text editor of choice with markdown.

### The Basics

Getting started with jekyll is relatively easy if you are used to using the command line. Assuming you have ruby installed, you can run these four commands and get right to developing!

{% highlight shell %}
gem install jekyll
jekyll new my-awesome-site
cd my-awesome-site
jekyll serve
{% endhighlight %}

That's it! Jekyll defaults to [localhost:4000](http://localhost:4000/) for it's development server, so navigate your way there to see what it's built for you.