---
layout: manual
title: Maintaining version control in coding
published: true
---

When contributing to the project start your development in a separate branch. Please take close attention of the branching conventions stated below. 

## branching model: gitflow

The develop branch is default and is where the developed features will be merged in. Off this develop branch feature branches can be branched to develop functionality. The master branch is a direct representation of what's released on production. 

Detailed in formation on Gitflow can be found on [gitflow, a successful git branching model](http://nvie.com/posts/a-successful-git-branching-model/)

## branching

The typical workflow is that you get a ticket assigned. For future reference in the git history, this ticket reference needs to be reflected in both the branch as in the commit message. 

Example of branch name when working on a ticket:

$ git checkout -b "prjct-x_ticket-name-hyphend"

Where 'prjct' stands for project, and the first letter from each word in the project's name will be used for the prefix. The x stands for the ticket number. After the underscore is the ticket's name. 

- Example of github ticket system, gh: gh-3\_create-git-guidelines
- Example of JIRA ticket system: DSG-1245\_create-polymer-integration

projects:
- lowercase project name: 'gh' = Github project: Tickets in the issue list of the repo
- Uppercase project name: 'DSG' = project: Dorel Style Guide

Mergin branches will always have to be “git merge --no-ff” to always keep the reference to the original pull request in our commit history.

## git history

The git history should be readable, traversable, and flexible enough to operate on. You must make logical commits regularly to create a logical timeline. Only use history changes on commits that you haven't shared with anybody.

### commit messages

Having a good commit timeline will speed up the reviewing process and help write a good release note.

Keep in mind that making a commit means making a set of changes permanent. Also a diff will tell you _what_ changed, but only the commit message can properly tell you _why_.

Start a commit message again with first the ticket number. 

Write the commit message in imperative. Typical commit message start with "Add..", "Fix..", "Rework..", "Enable..", "Replace..", "Polish.." etc.

## git paticipation

Two types of developers

- contributor: contributes to the repository
- maintainer: maintains the git repository

### contributor
Typical actions for the contributor are: Starting of a branch, filing in Pull Requests.

### maintainer 
Authors the code of the contributor before it's merged. 
Typical actions for the maintainer are: Review Pull Requests. 
