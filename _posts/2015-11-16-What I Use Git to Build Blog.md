---
layout: post
title:  What I Use Git to Build Blog
date:   2015-09-06 14:06:05
categories: Jekyll
excerpt: Web App 相关技术，移动端的 web 应用
---

# What I Use Git to Build Blog

First git repository is empty.

So we should first add and commit to init the master branch.

After above, you could make a new branch.

init a new branch

` $ git branch testing`

show all branch

` $ git branch -a `

check what status it is now

` $ git status `

This article is really detailed.
[http://blog.jobbole.com/25808/][1]

` $ git checkout —orphan gh-pages `

` $ git add . `

` $ git commit -m "first post" `  

` $ git remote add origin https://github.com/username/projectName.git `

` $ git push origin gh-pages `

---- Finally, I found it.
[http://tindlewei.github.io/WeiBlog/][2]

What Helped me. 
[http://www.aymerick.com/2014/07/22/jekyll-github-pages-bower-bootstrap.html][3]

Oops, I installed bower [https://github.com/bower/bower][4]
Also installed grunt [GRUNT][5]

[1]:	http://blog.jobbole.com/25808/
[2]:	http://tindlewei.github.io/WeiBlog/
[3]:	http://www.aymerick.com/2014/07/22/jekyll-github-pages-bower-bootstrap.html
[4]:	https://github.com/bower/bower
[5]:	http://gruntjs.com/