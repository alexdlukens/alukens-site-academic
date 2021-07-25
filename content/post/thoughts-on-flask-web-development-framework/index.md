---
title: Thoughts on Flask Web Development Framework
date: 2021-07-25T20:45:03.067Z
draft: false
featured: false
categories:
  - Python
  - WebDev
projects:
  - idea-shop-webapp
image:
  filename: featured
  focal_point: Smart
  preview_only: false
---
Throughout th Summer of 2021, I have been working with developers at the [Idea Shop Prototyping Lab](https://ideashop.iit.edu/) to improve upon the functionality and aestetics of the Idea Shop's Web App interface. This interface is used for serving videos, providing quizzes to students, providing real-time shop status information, and acting generally as a landing page for visitors to the Idea Shop.

At first, I did not believe that the Flask framework--which runs on Python--would be performant enough, however I have been throughly impressed with the responsiveness of the site. The site, which will primarily be served to students on campus, successfully queries a MariaDB database, dynamically generates webpages, and transmits these pages to the user with loading times under 300ms. This is more than adequate for the use case it is needed for, but I worry about the scalability of such a solution.

It is to my understanding that when the site moves from a "Development" runtime to the "Production" runtime that performance will further improve, although it is unclear how much this will impact the site. 