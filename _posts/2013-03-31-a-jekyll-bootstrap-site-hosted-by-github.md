---
layout: post
title: "A Jekyll Bootstrap site hosted by GitHub Pages"
description: ""
category: 
tags: []
---
{% include JB/setup %}

How to install [Jekyll Bootstrap](http://jekyllbootstrap.com) on [GitHub Pages](http://pages.github.com) for your project?

### Create a new _gh-pages_ branch in your repository

    git clone https://github.com/username/projectname.git
    cd projectname/
    git checkout --orphan gh-pages
    git rm -rf .

### Inject _Jekyll Bootstrap_ into your local repository

    cd ..
    git clone https://github.com/plusjade/jekyll-bootstrap.git
    cd jekyll-bootstrap/
    rm -Rf .git
    mv * ../projectname/.
    mv .gitignore ../projectname/.
    cd ..
    rmdir jekyll-bootstrap/
    cd projectname/

### Customize _Jekyll Bootstrap_

    rm -rf _posts/core-samples
    vi _config.yml

You might want to modify the _author :_, _title :_ and _tagline:_ sections.

Modify your index page: `vi index.md`.

_Jekyll_ accepts Markdown and HTML as input formats. You can even mix them in one file.

It then uses templates to render the final static pages, in the `_site` folder.

You can test locally your website, just by typing `jekyll --server` and then navigating to <http://localhost:4000> with your favorite browser.

They are many other things that you can do with _Jekyll_ and _Bootstrap_ to create the best blog or website ever. Please refer to official documentations for more details.

### Publish to _GitHub Pages_

Once you're ready to publish the very first version of your website.

    git add *
    git add .gitignore
    git commit -a-m "Initial commit"
    git push origin gh-pages

Then it's time to be patient, comb your unicorn or call your ex, because GitHub may take several minutes before "jekyllizing" your _gh-pages_ branch.

Finally, your website should be online: <http://username.github.com/projectname/>

You can now start to update your website:

* Add new pages: `rake page name="about.md"`

* Add new posts: `rake post title="Hello World"`

* Test you site locally and then push commits to your project's `gh-pages` branch on GitHub.

### DNS tricks

If you have a domain name you can even point it (or a subdomain of it) to your GitHub pages.

#### Entire domain pointing on _GitHub Pages_

In your registrar control panel, create or modify an `A` entry to make it point to _GitHub Pages_ servers.

    mydomain.org             A       204.232.175.78

In your `gh-pages` branch create a _CNAME_ file containing the name of your domain: _mydomain.org_.  

#### Point a subdomain to _GitHub Pages_

In your registrar control panel, create or modify an `CNAME` entry to make an alias of _username.github.com_.

    mysubdomain.mydomain.org          CNAME   username.github.com

In your _gh-pages_ branch create a _CNAME_ file containing the name of your subdomain: _mysubdomain.mydomain.org_.  

This even allows you to have multiple subdomains to point on the different _GitHub Pages_ of your multiple projects: 

* from your registrar point of view the different `CNAME` entries will point to the same target (username.github.com)

* but in your different _gh-pages_ branches, the _CNAME_ files won't be identical because containing different subdomains (mysubdomain1.mydomain.org, mysubdomain2.mydomain.org...).

#### What about GitHub users or organizations?

If you want _GitHub Pages_ to host websites linked with your GitHub user or organization, create a new repository named _username_.github.com and push your _Jekyll Bootstrap_ contents into it instead of a _gh-pages_ branch of an existing repository.

For more details on this DNS magic, refer to [_GitHub Pages_ help](https://help.github.com/articles/setting-up-a-custom-domain-with-pages).