---
published: false
title: Jekyll blogging reference and perfect workflow guide
layout: post
tags: [Jekyll, Workflow]
categories: [Workflow]
---
I've used several blogging software in the past few years but none of those heavy-weight champions suited me, these software include wordpress, tumblr and movable-type.

In this post I'll explain why I choose jekyll for running this blog you are reading now and how you can have perfect workflow with jekyll.

<!--more--> 
A bit about my experience with other frameworks.
I liked simplicity of setting up wordpress, setting up movable type was easy too but not as easy as wordpress. I liked that movable type generate static files and deploy the website. but somehow I didn't stick with any of above frameworks, Somehow I get the feeling that I'll stick with jekyll and I made a right choice.

Why jekyll is perfect choice for me
-----------------------------------

> Jekyll is a simple, blog aware, static site generator. It takes a template directory (representing the raw form of a website), runs it through Textile or Markdown and Liquid converters, and spits out a complete, static website suitable for serving with Apache or your favorite web server. 

I tried many platforms as I said earlier, to test which blogging platform works best for me.
After trying several frameworks and using them for some time, I found out few things about myself and my blogging:

- 	I don't write too many posts, I write rarely
- 	I want control, more is better. I don't care if some things are hard to do, more challenging is better.
- 	I've seen a lot of user interfaces of blogging frameworks. When I wrote posts in them I found out that I use source code editor not the wysiwyg editor of these frameworks. I liked that movable type supports markdown and other styles. Wrote a post or two in mt and loved it and found out that I actually hate writing text on those textareas. I thought it can be made better and then I found out about jekyll. Simply the idea of writing posts in my favorite text editor sublime text is awesome, you can choose whatever editor you like. I spend my most of the time writing code in it anyway.
- 	Everybody or most of the people are using wordpress, tumblr, mt or other similar software. What is different or exciting about that? Jekyll is different.

So I'm using jekyll now and it's easy, at least after you manage or setup things the way you want and have a good workflow.

Perfect workflow with Jekyll
----------------------------

I've used jekyll-bootstrap to setup my jekyll blog( Qubit Logs ). So here is how I use jekyll to post on this blog.

+ 	### Launch Terminal
	
	I open the terminal and cd into my jekyll directory

+ 	### Generate post

	to create a new post, I type following command
```
rake post title="title of the post"
```
A new file is generated into the <code>_posts</code> directory

+ 	### Open your favorite editor

	Launch your favorite editor to write the post. I prefer sublime text 2. I've setup my project file in sublime, which I'm including below.
```
{
 "folders":
 [
  {
   "path": "/Users/rajsinghrathore/Sites/qubitlogs",
   "folder_exclude_patterns": 
   [
    "_assets", "_includes","_layouts", "_plugins", 
    "_site", "img"
   ],
   "file_exclude_patterns": 
   [
    "_config.yml", ".htaccess", "archive.html", "atom.xml", 
    "robots.txt", "index.md", "categories.html", "tags.html", 
    "changelog.md", "pages.html", "Rakefile", "README.md", 
    "sitemap.txt", "Gemfile", "Gemfile.lock"
   ]
  }
 ],
 "settings":
 {
  "tab_size":2
 }
}
```
It has two advantages
1. 	I only see the files I want to see and everything else is hidden
2. 	Whenever I'll want to write a post I can switch to my blog project from project menu and create a post by creating properly named file and adding proper YAML front matter.

+ 	### Add proper front matter

	I have customized my jekyll blog a lot and now it supports a lot of varibles, I'm including some variables below with some sample data, for my own reference. I don't want to forget these varibles as I may need them a lot in future
```
layout: post
title: "Jekyll blogging reference and perfect workflow guide"
tagline: "Why jekyll is awesome"
description: ""
category: Workflow
tags: [Jekyll, Workflow]
sharing: true
comments: true
robots: index,follow
alias: [/lessons/2012/1/20/jekyll-introduction/index.html]
date: 22 January 2013
published: true
```
+ 	### Generating Post in <code>_site</code> directory

	to generate post run following command in terminal
```
jekyll --server
```
+ 	### Deploying the website

	Here is a tricky part, lots of the option available to use. I tried using post-receive hook and it worked but needed to write a lot of mod_rewrite rules to direct to <code>_site</code> directory. Another choice was to install jekyll on my server too and generate <code>_site</code> directory in my main directory. But didn't like it. I like to keep things simple.
	So here is what i do
	1. 	I have initialized git repository on my local machine and pushed it to remote repository, so that I have everything backed up.
	2. 	To deploy my website I have created a rake task, I'm using rsync to deploy
	
```
task :deploy do
  sh "rsync -avz --delete _site/ path_to_directory_on_your_server"
end
```
replace **path_to_directory_on_your_server** to appropriate value in above code 
then run <code>rake deploy</code> command in your terminal to deploy to your server.

This is my first post on Qubit Logs. I hope, I'll continue to write posts on this blog.
I hope this article works as a good reference to me, helpful and good resource to you. Please share it or bookmark it for future reference.

if you have some ideas or queries comment below.

Thank you for reading this far.