---
layout: manual
title: Maintaining version control in coding
category: Make software
draft: false
---

When contributing to the project start your development in a separate branch. Please take close attention of the branching conventions stated below.

## git workflow

The preferred branching model is gitflow. The develop branch is default and is where the developed features will be merged in. Off this develop branch feature branches can be branched to develop functionality.

The master branch is a direct representation of what's released on production. New releases (in Master) should be tagged following the [Semantic Versioning 2.0.0](http://semver.org) standard.

Example: `v0.0.1`

Detailed in formation on Gitflow can be found on [gitflow, a successful git branching model](http://nvie.com/posts/a-successful-git-branching-model/)

## git participation

Two types of developers

- contributor: contributes to the repository
- maintainer: maintains the git repository

- contributor: Typical actions for the contributor are: Starting of a branch, filing in Pull Requests.
- maintainer: Authors the code of the contributor before it's merged. Typical actions for the maintainer are: Review Pull Requests.

## branching

The typical workflow is that you get a JIRA ticket assigned. For future reference in the git history, this ticket reference needs to be reflected in the commit message as described in the next chapter *git history* title. But these commits will also need to be contained in a encapsuled version of the repository so you can work freely without interferring with other developers. For that you can create a branch.

When branching a specific task, use the dedicated branch folders. Example of branch folders:

- feature/..
- bugfix/..
- release/..

projects:

- Lowercase project name: 'gh' = Github project
- Uppercase project name: 'DIO' = dorel.io project in JIRA

For a feature:

- Example of JIRA ticket system: `feature/kitchensink` (feature name)

The kitchensink is a dedicated page meaning that the work can be encapsuled on a single branch. Multiple tickets can be comitted in this branch which allows for solving multiple tasks for that feature. The words in feature branches are separated by hyphens.

For a bugfix:

- Example of JIRA ticket system: `bugfix/DIO-124`

Bugfixes can be created as a single branch with the branchname of the bugfix. That way you can work on it encapsuled, and there's always a reference back to the ticket in which information is stored. 

For external logged bugfixes (exception):

- Example of Github ticket system: `bugfix/gh-1`

Mergin branches will always have to be `$ git merge --no-ff` to always keep the reference to the original pull request in our commit history.

## git history

The git history should be readable, traversable, and flexible enough to operate on. You must make logical commits regularly to create a logical timeline. Only use history changes on commits that you haven't shared with anybody.

It's recommended to have component names in the commit message so it's easy to track in the history when a new component is available.

### (smart) commit messages

Having a good commit timeline will speed up the reviewing process and help write a good release note.

Keep in mind that making a commit means making a set of changes permanent. Also a diff will tell you _what_ changed, but only the commit message can properly tell you _why_.

#### composition of a commit message

Start a commit message with first the ticket number.

Example commit message: `DIO-1 #comment Add highlight option #time 0d 1h #done`. Using smart commits, the there are a few commands you can pass through:
- comment: `#comment` part adds a comment directly to the ticket in JIRA.
- time: `#time` will state how much time it took to fix this ticket
- transition: `#done` The last command shows the transition of the ticket state. At the moment we only have three transitions: '#to-do', '#in-progress' and '#done'. Typically you'd only use the last command #done since the first two transitions are maintained in the JIRA board, and will be changed in the sprint meetings.

##### comment
Write the commit message in imperative. Typical commit message start with "Add..", "Fix..", "Rework..", "Enable..", "Replace..", "Polish.." etc.

##### time
Typically commits don't consist of work more than four hours. See for guidelines on how to compose a commit message

##### transition

These commands are not mandatory on every commit. However at your last commit, once you finish the ticket, use the last '#done' command. It's also possible to resolve multiple JIRA tickets with one commit using `DIO-1 DIO-2 DIO-3 #comment change setup of foo #time 0d 2h #done`

### commit message Githook

Dorel uses githooks. The githook checks if your message is correct and lets you change it in case you've made a mistake or have forgotten to mention it.

[Install the Dorel Juvenile webhook](https://github.com/dorel/git-hooks).

## Releases

Everytime a release to master is done it needs to be tied to a version number. Check [Semver](http://semver.org/) is used for this purpose.

TL;DR:

- MAJOR version when you make incompatible API changes,
- MINOR version when you add functionality in a backwards-compatible manner, and
- PATCH version when you make backwards-compatible bug fixes.

After the release has been released in origin master, make this released version 'Latest release' if applicable to have the repo reflect the latest version. See Githubs documentation for this [linking-to-releases](https://help.github.com/articles/linking-to-releases/)

---

## Tutorials

### 1. new feature/bugfix workflow

This tutorial assumes you're working using the terminal and that you have a basic understanding of Git.

1. Typically you get a JIRA ticket assigned to you. Check and make sure that the corresponding issue unique reference (DIO-x) is not already available in the existing branches. You can check this both in the JIRA ticket itself, to see if someone already comitted. Since it's a new issue ideally it shouldn't. Then perfom the next step.

```
// use fetch to get all remote branches
$ git fetch --all
// get overview of all the branches
$ git branch -a
// always do a git pull to make sure you've got the latest version
$ git pull
```

2. The next step is to create a branch with the corresponding ticket reference, by branching of off the develop branch. The -b prefix will create a new branch if the branch doesn't exist yet:

`$ git checkout -b feature/DIO-x develop`

3. Start working on the feature/bugfix. Gradually commit your changes as described in the previous chapter *git history*:

First stage the changes you've made:
```
// stage specific files
$ git add <filepath>
$ git add <anotherfilepath>
```

or

```
// stage all changes
$ git add .
```

Then commit the staged changes:

`DIO-1 #comment Add highlight option #time 0d 1h #done`

Keep repeating this step until your function is finished. Once you're done your branch is ready to be tested.

6. Move the changes you made to remote (a.k.a. origin):

`$ git push origin HEAD`

7. At this point open github.com and the correseponding repository. Make a pull request and assign this to another developer to review. Once the other developer sees no mistakes he/she will merge the pull request and your code will be in the develop branch.

### 2. Doing a release

Always work from the develop branch:
`$ git checkout develop`

Make sure you have the latest changes:
`$ git pull`
`$ git checkout -b release/0.4.0 develop`

Tag the commits *with an annotation* making it a solid commit (as opposed to a lightweight tag). An annotated tag always has tagger (author) and date. This will make it show up in the overview:

```
$ git checkout master
$ git merge --no-ff release/0.4.0
```

Tag the commit:
`$ git tag -a 0.4.0`

_Additional information on source: [what-is-the-difference-between-an-annotated-and-unannotated-tag](http://stackoverflow.com/questions/11514075/what-is-the-difference-between-an-annotated-and-unannotated-tag)_

Then push the tags:
`$ git push --follow-tags`

```
$ git checkout develop
$ git merge --no-ff release/0.4.0
$ git branch -d release/0.4.0
```

Push all the branches:

```
$ git push origin master
$ git push origin develop
$ git push origin --tags
```
