---
title: "Viscon Hackathon 2021"
date: 2021-10-22T15:33:29+02:00
draft: false
toc: true
images:
tags:
  - Hackathon
---
After having finished a year of ETH I believed myself to be able to muster any problem thrown my way. After hearing from our student association, vis, that they were hosting a Hackathon at their VIScon, we signed up immediately. This was all of our first time participating in any kind of such competition and much like with this post, we didn't really know what we were doing. I gathered four of my friends, some of whom were better programmers, and we dove in head-first.

# Challenges and organization
This hack was hosted at our university in the libraries and lecture halls. It started on a Friday afternoon, and we were soon introduced to the framework of this hackathon. Our task was to facilitate the life of our students through services that could be implemented by the student association. 

I do not quite recall all the challenges that one could choose from, but this should present a rough overview:
One challenge consisted of creating a web app which, using a pretrained model, one could input the recording of a lecture, and it would present you with a summary of the contents of the lecture, cut down to a rough length determined by the user.

Another challenge prompted you to remake the vis poster collection and to implement new features such as a search feature.
Yet another challenge was to create an infrastructure finder application for our campus. The university does provide maps, but they are hard to read at times, do not include all the facilities and don't really show you the way to the desired destination. This ended up being the challenge that we chose.

# In the beginning
The beginning was optimistic, as all hacks are. High spirits, free mate, beer and food were some of the highlights. We quickly got started brainstorming for the structure of our website. Once we got settled on the structure and the design, we discussed how we would implement this. We decided that we were going to use next.js, which gives us a wide range of useful features, for our application in the frontend and mongoDB as our backend solution. 

As a team of 5 we had a good amount of manpower, we only needed to correctly split up the tasks to ensure efficient completion of the tasks. We decided to split up the tasks as follows: 2 of my friends and I would be responsible for the frontend implementation, and the other two (who were significantly more experienced than either 3 of us) would be responsible for the backend and troubleshooting the inevitable problems that would arise. I furthermore took on the responsibility as team lead and kept an overview of who was doing what and where we stood with each part of our application. We were all very excited to get started, and we dove right in.
{{< figure src="/images/IMG_2906.jpg" width="500px" caption="A picture of us working, the only team that brought an ultrawide monitor.">}}
I got started on creating a landing page. Drafting up a first version didn't take too long, little did I know, though, that this was far from the final product.

During the hack, we had a few mentors who were there to help us with any problems that we might have. They were very helpful, and we were able to get a lot of help from them. Among others, there was a UI/UX expert from beekeeper. He managed to give me a lot of insight on what goes into the design of a website and how to make it more appealing to the user. He also gave me some tips on how to make the website more responsive and how to make it look better on mobile devices. I was very grateful for his help and I learned a lot from him.

In the end, the landing page was remade/tweaked about a dozen times.

# Our application
The actual application to find amenities on campus took more time. The first challenge was to get the location of the amenities. Unfortunately, the university does not provide a public API for this, so we had to scrape the data from the university website. This was a bit of a challenge as the website was not very well-structured and the data was not easily accessible. We managed to get the data though, and we were able to get the location of the amenities.

The orientation inside the building was the next challenge. It is VERY challenging to locate the user in a 3 dimensional space. We thought of a few different approaches, but none of them were feasible to implement. We ended up letting the user select his location himself, inputting the building, floor and closest room number.

The last piece of the puzzle was to find the way from our current location to the closest (functional) selected amenity. Our suggest approach was to implement a coordinate grid on top of the maps and use a pathfinding algorithm (such as A*). We quickly had to scrap the idea of actually coding this up, since that would have been  outside the scope of this hackathon.
For the demonstration, we decided to hard-code some locations and the corresponding paths. This was not ideal, but it was the best we could do in the time we had.

# The result
After 36 grueling hours (and a collective amount of 7 hours of sleep over two nights) we got to presenting our finalized product. We were very proud of what we had managed to build in this timeframe.

When it came to the judging, we were not expecting much. We were however one of the few teams that had a working demo.
We ended up getting 2nd place in the hackathon, which was a huge delight for us. Not only that, but we also managed to snag a few wins, including best commit message, the best Lego creation and best readme.
{{< figure src="/images/stats.JPG" width="600px" caption="Awards for various aspects">}}
{{< figure src="/images/best_commit.JPG" width="600px" caption="The best commit messages.">}}
# Summary
These 36 hours were an incredible experience for me. I managed to learn a lot about web development and got to meet a lot of new people. I am very grateful for the opportunity to participate in this hackathon, and I am looking forward to the next one.

It showed me that for an application to work, a lot of coding, designing, rewriting and scrapping is required.