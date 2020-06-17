---
layout: post
title: Everything related to maintaining this Blog - Nuts and Bolts
tags:
  - howto
description:
published: true
---

This is not an article. I am simply building a catalog of notes that are useful when updating this blog. Because the entire code has to be altered, it is useful to include some technical details. I forget details too often.

*Last Updated: June 6th, 2020*

<!--break-->

**Important Update:** The length of the article must be quite long for the tags to be clickable, on the blog page.

# How to Build the Site
Building the site with jekyll is done everytime I want to see the changes I made to the blog.
Every time I open the project, I must first export the 'gems' that are located in my local machine:

First, run
`export GEM_HOME=~/.gem`

Then, run
`export PATH=$HOME/.gem/ruby/2.6.0/bin:$PATH`

This is personal to my local machine, so it must be different for other users.

Now, build/update the website by running `bundle exec jekyll serve`. Then, the '_sites' folder must be updated, and it is ready to be uploaded to GitHub.

# How to put a break to an Article

Include `<!--break-->` to create a break in the article.

# How to Create a Tag

This is a simple process. I used to create a separate 'permalink' for each and every tag, but for this blog, I just need to create an `.md` file.

Under the `_my_tags` folder, create an `.md` file with the name of the tag.
Then, inside the file, input the following format:

<script src="https://gist.github.com/SangwookCheon/c56017d6abc92980193b3f4e479fc941.js"></script>

# Code Syntax
As of now, there's a problem with Code Syntax. The UI crashes when published to GitHub, while it works locally. So, I need to create a better version or use an external tool for code blocks.

Until this is fixed, let's just use GitHub gists. They are a little bit tedious to create, but they work really well.

# If I want to exclude Pictures and Snippets from the Main Blog Page

In the `blog.html` layout, include the following snippet of code:

<script src="https://gist.github.com/SangwookCheon/77cafb84c4d4d28101da67b1dca64d60.js"></script>

# How to Change the Style of Titles of Articles (When reading them)

Go to `_titles.scss` file, look for `.post-title-container` in that file. This contains information on how the "title" section (both on the blog page and post) should look like. I can change color, font size, font family, etc. Actually, this scss file contains everything about titles, subtitles, and how an article should look like. So tinker with the components.

# How to Change the Color Scheme of the Whole Blog

Here are the things I can change:
  - When text is selected via mouse drag, the selection background color
  - Color when Hovering on Links
  - Color of the Horizontal Rule

For the first one, go to `_base.scss` and search for `::selection` Here, I can easily change the color as well as effect.

For the second one, go to `_base.scss` and find `.a` which is a shorthand for links.

For the third one, go to `_base.scss` and find `hr`.

Yes, so everything related to color can be found in this scss file.

# Problems I need to Fix
* On a mobile phone, the title of an article is too big when I click on the link to that page. I must make the font size adapt to screen size
* I want to make a search function that instnatly shows results, like the TeXT theme.
* I need to enable pagination for the "creatives" tab. Currently, it's not working.

# Things I want to Improve On
* Improve the search function so that it doesn't lead to a DuckDuckGo page.
* Create a platform where I can input any kind of html file as a post --> greater flexibility, like New York Times interactive articles.
