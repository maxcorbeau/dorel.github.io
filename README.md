# dorel.github.io
Dorel.io Website

Notes: 
- GitHub pages enabled
- url: http://www.dorel.io/
- uses Jekyll to generate pages

# Run Jekyll locally

## Dependencies

- ruby version 2.X.X
- bundler

## Generate Jekyll site files locally

To build your Jekyll site locally, preview your site changes, and troubleshoot build errors, you must have Jekylll site files on your local computer. This allows you to preview changes before they are comitted to the repo. 

The local files for https://dorel.io are stored in ./source/site/..

### Steps to run local server

Run `$ bundle install` to install all the gems.

Run `$ bundle exec jekyll serve` to start the local server.

This will compile the source/site/.. folder into a *temporary* folder '_site'.

Now the following url can be used in your browser to see the pages locally: `http://localhost:4000/`. Changes made to the source/site files will be reflected on this url automatically.
