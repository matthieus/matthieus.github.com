---
layout: post
category: Software is Made by People
---
{% include JB/setup %}

Making good software is difficult, but not for everybody. Some people, often small teams or lone developers, will create true gems which can be tenfold better than what a company on a large budget will release. I could give examples like the first Unix and most computer languages, but you all have seen some brilliant piece of software written by one guy, or a small team that worked particularly well together. How can this be reproduced?
When making software, if you want to make a user happy you have to think like him, you have to *be* the user. From that logic, you realise quickly the ideal world is a developer developing software for himself. Or developers developing for themselves. And most of the time that's when good software is made.
But not all software needs can come from the people who will develop it. So how can we at least make the product team develop like it was creating a product for themselves?
To answer that question, we will start from a standard project and see how we can work our way towards a product team which will behave more like a team of future users.

Let's take a look at a scenario where a random software company makes software for other companies, not an uncommon scenario. We'll assume the software company is building a new product from scratch to help a client replace a set of Excel sheets by a full blown application bringing standardized processes and data. Because they were in contact with that particular line of business, a few people in the software company have a vision of what the product can do better than other products. But for the details, our company will rely only on its relations with the client to know what exact feature will go in the future product. <br>
A project plan could be:
0. Client likes the vision of the software company and agrees to buy the future product and help its design 
1. Client creates a project team on its side, users are part of it in the limit of their availibility
2. Software company creates a project team, with a product owner, a project lead and developers.
3. Workshops are organised to flesh out the requirements
4. Development is done with some intermediary validations from the client in a pseudo-Agile way (pseudo because the product is never deployed in production for these intermediary validations)
5. Final delivery going live is done after 1 year of development
<br><br>
Let's assume everything went well: the client was relatively mature about what he wanted, the specifications were as good as a specification can be, the development team worked well together. A lot of people will say that's a very lucky project, but the point of this article is not there, it is whether the product is good or not.

The process described above is a standard, proven by the market, way to make software. Billions are made by software companies which sell software made this way, SAP being the first and best example for that model.

But this kind of software doesn't make users consistently happy. They will still have bouts of nostalgia for the Excel sheet being replaced. What will be missing is an efficient way to do common things, some flexibility when needed, and some consistency throughout all the features. Usability will also be an issue. The whole application will feel like there could have been some maturation. It's important to note that this is usually fine as the benefit of having a standard application throughout the company is a great step forward for reliability and reporting capabilities.

This is not brilliant software though. The brilliant software should make the user forget about Excel and what he was using it for. The makers are far too far from the users and their detailed needs. And conversely the users telling what they want are far too far from the product team, which was the owner of the starting vision after all. Requirements go from one side to the other, but it only brushes over the core concepts behind the application. Meetings tend to focus on details instead of the broader picture and consistency of the application. The reason for that is that neither the users or the product team understand deeply what the other side really have in mind.

The makers can't guess all the things going through a user's mind when he completes a task. The users can't guess the general design choices made by the makers. Makers are not trained to be users, and users are not trained to be software designers. And to make good software, we need that to happen, in some way.
In the organisation described above, even if the teams are small, there are too many stakeholders, too many decision makers, too many intermediaries. The necessary iterative loops to improve features are simply too slow to reach mature features in a reasonable time frame. Making one software with two teams isn't going to be easy.

To reach maturity quickly, there is only one way, the makers need to *be* the user, and conversely the users need to *be* the makers. How can this happen? Asking the question is half the answer: the users need to be part of the development team. Users using the software with their own data that they know and understand, users having ideas directly discussed with the product owner and developers, users understanding the logic behind a software product making, this is what the user should do in the product team. Makers watching the users using the software, makers creating new scenarios of usage and testing them with the users, makers testing prototyped features on users, this is what the makers should do when designing the product. And this has to be an ongoing process throughout the whole life of the software.
That kind of teamwork can make features maturity gain years compared with a process involving more intermediaries.

How could such a process work when it involves two companies with completely different goals? I don't know anything about partnership or consortium, but I feel that's what b2b software products need, partnerships. Partnership is not easy of course, and there are some governance and revenue considerations to take into account. But let's not forget the target of all the work being done: users of the software being made need to get more efficient at what they do.

**Note:** Going this direction raises an important question about the fact the software needs to be sold to other clients. How do we introduce genericity when we have users with a very specific requirement sitting beside us? I think the requirements are never as specific as we think. Specific requirements are often one particular solution to a generic problem which is shared by many other companies. There is a general rule called the "rule of three" which can typically be used here: do it once, do it twice, genricize the third time.
