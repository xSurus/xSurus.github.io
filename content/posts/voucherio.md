---
title: "voucherio --- Viscon Hackathon 2022"
date: 2022-12-21T16:28:11+01:00
draft: false
toc: false
images:
tags:
  - Hackathon
  - WebApp
  - Personal project
technologies: 
  - Next.js
  - PostgreSQL
  - JavaScript
  - TypeScript
---
Our student association recently hosted a hackathon with the goal of creating a voucher marketplace for businesses (henceforth referred to as suppliers). The idea was to provide a platform for businesses to offer discounts and promotions to groups (henceforth referred to as seekers) and to thus simplify the purchasing of such amenities. The hackathon was a great success, with a diverse group of students coming together to work on the project. We were amazed at the creativity and dedication of the participants, and were proud to see the finished product take shape over the course of the weekend.
## The Challenge
The voucher marketplace that was developed is a web-based platform that allows suppliers to create and post vouchers for seekers to purchase. Seekers can browse the available vouchers and purchase them. The vouchers can then be redeemed at the participating businesses, providing a convenient and cost-effective way for seekers to find vouchers for their events (such as this hackathon).
## How it works
For the frontend, we used the Next.js framework to build a responsive and user-friendly interface for the voucher marketplace. Next.js is a popular framework for building server-rendered React applications, and we found it to be a great choice for this project due to its ease of use and powerful features. On the backend, we used a Postgres database to store and manage the data for the voucher marketplace. Postgres is a widely used and reliable open-source database, and we found it to be a great fit for our needs. We used the Node.js runtime to connect to the Postgres database and perform various operations, such as creating, reading, updating, and deleting vouchers.

Throughout the project I took on the responsibility as project lead, and I was very happy with the results. This was one of the first times that I officially took on this role and I definitely faced new challenges. As project lead it was my responsibility to make the   to coordinate between the two members working on the backend with the other two members working on the frontend. I also had to make sure that the project was on track and that we were able to meet the deadline. To do that I had to identify and follow through on the crucial parts of the project and cut out aspcts that were not necessary. One of the compromises we had to undergo was the decision for the design of the payement system, which takes on a very tedious and time-consuming process.
## Features
voucherio has a number of features that make it a great tool for both suppliers and seekers. Some of the most notable features include:
* A user-friendly interface that allows suppliers to easily create and manage their vouchers
* A search function that allows seekers to find vouchers that match their needs
* A filter function that allows seekers to filter vouchers by category
{{< figure src="/images/orders.png" width="600px" caption="Overview of the orders page">}}
{{< figure src="/images/offers.png" width="600px" caption="Overview of the orders page">}}
One of the standout features of the voucher marketplace is the ability for businesses to customize their vouchers to suit their specific needs. This includes setting expiration dates, limits on the number of vouchers that can be purchased, and other parameters to ensure that the vouchers are used effectively.
{{< figure src="/images/filter.png" width="600px" caption="Example of the filter on offers">}}
## Improvements
We are proud of the work that we have done on voucherio, and believe that it is a great example of what can be achieved in a short amount of time. However, there are still many improvements that can be made to the project, and we hope to continue working on it in the future. Some of the improvements that we would like to make include:
* Improving the current payment system to allow seekers to purchase vouchers more easily
* Adding a statistics page to allow suppliers to view the performance of their vouchers
* Reworking the UI and theme the whole page
## Results
We are very happy with the results of the hackathon, and believe that we have created a great product that will be useful to many people. As with any other hackathon project, there are still many improvements that can be made, and we hope to continue working on the project in the future. It was a challenge, but, as always, a very welcome one.

We now began working with CAT, our student associations computer application team. The goal being to translate this project into production code that can be used by our student association. To do this we are in the process of reworking some of our backend code to make it more efficient and scalable. We are also working on the frontend to make it more user-friendly and to add some new features. We are very excited to see the finished product and hope that it will be a great success.