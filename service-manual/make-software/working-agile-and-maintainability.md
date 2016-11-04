---
layout: manual
title: Working Agile and maintainability
category: Making software
draft: true
---

## JIRA and Version control (Git)

Everything you do when working on code is for a reason. So in other words, you can always relate the code that you're creating to a subject. To manage the project and make decisions on what has the biggest priorities these subjects are separated in tickets. 

To associate commits with tickets ticket numbers are integrated within the commit messages. This way you have a clear commit historty of what's added for what reason.

As a rule of thumb, JIRA is used for the global overview. New features and components are stated and maintained in sprint plannings. Git tickets will be more about in depth technical related tickets. You're talking micro scoped tickets that would clutter the overview of a sprint planning in JIRA.

See the chapter (smart) commit messages in [Maintaining version control in coding](./service-manual/maintaining-version-control-in-coding.html) on how to write a commit message that ties in with the Agile workflow. 

## User stories
The goal of a user story is to deliver a particular value back to the customer. Note that "customers" don't have to be external end users in the traditional sense: they can also be internal customers or colleagues within your organization who depend on your team. User stories are a few sentences in simple language that outline the desired outcome. They don't go into detailed requirements.

<blockquote>
User stories are often written using the following template:

As a <type of user>, I want <goal> so that I <receive benefit>.
Let's use a website as a simple example to create a user story.

As a customer, I want to be able to create an account so that I can see the purchases I made in the last year to help me budget for next year.

User stories are sketched out by the product owner, and then the entire product team collectively determines detailed requirements.
</blockquote>

User stories are sketched out by the product owner, then the full product team collectively decide the more detailed requirements. These are the granular pieces of work that help define the implementation items for the story and the upcoming sprint. In the above example, there are a set of tasks required to make the account feature work: database changes, new server logic, as well as new user interface components. These tasks should be fleshed out during estimation of the user story and linked in the team's issue tracker.

## Epics
_Epics are significantly larger bodies of work. Epics are feature-level work that encompasses many user stories. Using the above example, an epic might be the entire account management feature and the ability to see previous purchases._

##Sprints
In scrum, teams forecast to complete a set of user stories during a fixed time period, known as a sprint. In Dorel.io we use sprints of a period of two weeks. This ties in with our bi-weekly newsletter.

Important to remember:
- Once a team forecasts a set of user stories for the sprint, and the sprint is started, the scrum master is in charge of fending off changes to the user stories. This keeps the team focused and combats "scope creep" (when a team adds work to the sprint after the sprint starts). Adding work mid-sprint compromises the team's ability to forecast and estimate accurately.
- At the end of each sprint, the team is required to deliver a working piece of software. In scrum, that's called a potentially shippable increment (PSI). The product owner ultimately decides when the PSI gets released to customers, but the work should be complete enough to be suitable for release at the end of the sprint. These PSI's can then be communicated through the newsletter.
- The items in sprints are not meant to be populated in advance. Before each sprint starts there is a meeting on what will be in the upcoming sprint.

Source and read more on the <a href="https://www.atlassian.com/agile/delivery-vehicles">delivery vehicles</a> page on Atlassian.com.
