# dorel.github.io

Master branch | Develop branch
--- | ---
[![Build Status](https://travis-ci.org/dorel/dorel.github.io.svg?branch=master)](https://travis-ci.org/dorel/dorel.github.io) | [![Build Status](https://travis-ci.org/dorel/dorel.github.io.svg?branch=develop)](https://travis-ci.org/dorel/dorel.github.io)

url: http://www.dorel.io/

Notes: 
- GitHub pages enabled
- uses Jekyll to generate pages

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
- ruby version 2.X.X
- jekyll 3.1
- bundler

Run `$ bundle install` to install all the gems.

Run `$ bundle exec jekyll serve` in the root folder (same where _config.yml) exists to start the local server.

This will compile the site's source files defined in the folder `source/site/..` into a *temporary* folder named '_site/', which in turn is used for hosting the site locally. 

Now the following url can be used in your browser to see these pages locally: `http://localhost:4000/`. Changes made to the source/site files will be reflected on this url automatically.
