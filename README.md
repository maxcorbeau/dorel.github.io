# dorel.github.io

Notes: 
- GitHub pages enabled
- url: http://www.dorel.io/
- uses Jekyll to generate pages

# Github pages

https://www.dorel.io is hosted via GithubPages. Configuration for this is stated in _config.yml. To make the site accessible via the custom URL 'www.dorel.io', a CNAME record has been added in the CNAME file.

# Run Jekyll locally

Having the site (Jekyll) available locally allows you to:
- preview changes before they are comitted to the repo
- preview your site changes
- troubleshoot build errors

## Dependencies

- ruby version 2.X.X
- bundler

## Generate Jekyll site files locally

Run `$ bundle install` to install all the gems.

Run `$ bundle exec jekyll serve` to start the local server.

This will compile the site's source files defined in the folder `source/site/..` into a *temporary* folder named '_site/', which in turn is used for hosting the site locally. 

Now the following url can be used in your browser to see these pages locally: `http://localhost:4000/`. Changes made to the source/site files will be reflected on this url automatically.
