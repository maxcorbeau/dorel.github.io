# dorel.github.io

url: http://www.dorel.io/

Notes: 
- GitHub pages enabled
- uses Jekyll to generate pages
- uses bower for package dependencies

# Github pages

https://www.dorel.io uses [GithubPages](https://pages.github.com/). So the pages are hosted directly from the github repository.

Configuration for this is stated in _config.yml. A CNAME record has been added in the CNAME file to make the site available via the custom URL 'www.dorel.io'.

# Jekyll

[Jekyll](https://jekyllrb.com/) is the static site generator used to transform the markdown files into html webpages. 

## Run Jekyll locally

Having the site (Jekyll) available locally allows you to:
- preview changes before they are comitted to the repo
- preview your site changes
- troubleshoot build errors

### Generate Jekyll site files locally

**Dependencies**
- bower
- ruby version 2.X.X
- jekyll 3.1
- bundler

Run `$ bower install` to install all the dependencies.

Run `$ bundle install` to install all the gems.

Run `$ bundle exec jekyll serve` in the root folder (same where _config.yml) exists to start the local server.

This will compile the site's source files defined in the folder `source/site/..` into a *temporary* folder named '_site/', which in turn is used for hosting the site locally. 

Now the following url can be used in your browser to see these pages locally: `http://localhost:4000/`. Changes made to the source/site files will be reflected on this url automatically.

## Jekyll collections

A collection can be seen as a grouping of similar document types. Jekyll provides 2 native document types: `posts` and `pages`. (mind the specific characteristics of each post type).

- posts
- pages

Beside that the service design guide for Dorel contains the following document types: 

- service-manual
- helping-people-to-use-your-software
- internet-of-things
- strategy
- technology
- user-centered-design

These document types will all have to live in the root `./site`. Even if one collection is a subsection of another. Which is the case with all the collections Dorel uses, every folder except 'service-manual' is supposed to be a sub-section of the `_service-manual`. One of the prerequisites of a collection is that it starts with a underscore.  
In the \_config.yml file is stated how the permalink structure should work. In that file for example you can see that all these collections have a _permalink:_ parameter set to `/service-manual/:foo/:bar`. 



