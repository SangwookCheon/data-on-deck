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

<!–-break-–>

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

```
  ---
  slug: name (all lowercase)
  name: name (this appears in the tag page)
  description: optional
  ---
```

# Code Syntax
As of now, there's a problem with Code Syntax. The UI crashes when published to GitHub, while it works locally. So, I need to create a better version or use an external tool for code blocks.
