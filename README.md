# Source code for lukasbommes.github.io

This repository contains the source code for my home page at [lukasbommes.de](https://lukasbommes.de/)

### Prerequisites

To build and update the website jekyll needs to be installed as per this [documentation](https://jekyllrb.com/docs/installation/).

### Deploy the website

Clone the repository into `/var/www/lukasbommes.de`. Then, install requirements with
```
bundle install
```
and build the website with
```
bundle exec jekyll build
```
Deployable artifcats are found in the `_site` directory.

### Local development

You can serve the website locally with
```
bundle exec jekyll serve
```
