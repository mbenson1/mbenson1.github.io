---
layout: post
title:  "The Bloggining! A Jekyll Tutorial"
date:   2017-04-11 10:01:35 -0700
---
I’ve been hearing a lot of goods things about Jekyll for a while now. The idea of stepping away from the more complicated CMS like Wordpress that I’ve used in the past seems appealing for a simple site. The project I had in mind (this site) was a blog to catalog or document various projects in a single location which sounded perfect for what GitHub Pages and Jekyll had to offer. One thing that made this setup slightly more complicated was the desire to have a site that I could modify and serve locally to then push to GitHub Pages. The easier route since GitHub Pages is integrated with Jekyll would be to setup a github page, choose a theme, and add some posts.  
### [](#header-3)Installing Ruby, Rubygems, and Jekyll (Ubuntu)
At the time of writing this, Jekyll needs version 2.0 and the apt “ruby-full” package provides Ruby 2.3. I should probably be using a Ruby version manager like rbenv or RVM but oh well. The --user-install flag installs the gem inside the home directory. Running gem environment will tell you where the user installation directory is to add it to your path.
```bash
$ sudo apt-get install ruby-full
$ sudo gem update --system
$ gem install jekyll --user-install
$ gem install jekyll bundler --user-install
$ gem environment
$ export PATH=$PATH:/home/username//.gem/ruby/2.3.0/bin
```
### [](#header-3)Creating a Site and Selecting a Theme
The easy part is the following three commands which create a new Jekyll site and serve it on the preview server.
```bash
$ jekyll new myblog
$ cd myblog
$ jekyll serve myblog 
```
And the site is up at localhost:4000. Wasn’t that easy compared to setting up a LAMP server! Since I want the midnight theme I replaced “minima” in the gemfile with “jekyll-theme-midnight” and theme: jekyll-theme-midnight to the _config.yml file. Before building with the new theme a couple of changes need to be made to the default site because not everything supported in the default theme minima is supported by midnight. I primarily made the following changes:
1.  Deleted with the about.md file.
2.  Copied the post.html and home.html layouts from the minima theme.
3.  Added a defaults.html layout from the midnight theme and made some small changes. The defaults.html in _layouts (as well as any other files with the same name) will overwrite the defaults.html in the gem file.
4. Added some custom share icons based on the article [here](http://tomhohenstein.com/Jekyll-Custom-Share-Buttons/) and a tiny bit of custom style to /assets/css/style.scss.  

The [Jekyll documentation](https://jekyllrb.com/docs/home/) on content creation as well as the themes own index.md provides almost all the information needed for blogging basics. 
```bash
$ bundle install
$ bundle exec jekyll serve
```
Now all that’s left is to push to a [GitHub Pages](https://pages.github.com/) site. 
