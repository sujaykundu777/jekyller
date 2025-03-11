# jekyller - Learn how to jekyll

Learn to build and host jekyll based sites using github actions and pages. Step-by-step instructions for begineers wanting to understand on how to use it.

### Jekyll


### Github Pages

GitHub Pages is powered by Jekyll, a static site generator, meaning sites deployed using GitHub Pages are built using Jekyll

[Github Pages Gem](https://github.com/github/pages-gem)

GitHub Pages currently uses Jekyll version 3.9.3, as the "github-pages" gem bundles that version

#### Learning Paths

- Build and run a jekyll site locally and using Github pages to host the built jekyll site.


#### Docs :

### local versions on build
specs: macbook m2 pro 32gb. MacOS vs. Sequoia 15.3 

ruby 3.3.4 (2024-07-09 revision be1089c8ec) [arm64-darwin23]

- Bundler version 2.5.15

### jekyll gems related :
`gem install jekyll -v 3.9.3`
`gem install bundler`
`gem update bundler`
`gem pristine --all`

Important: Make sure you have Bundler > v1.14 by running gem update bundler in your terminal before following the next steps.


### Bootstrap a new jekyll site

Running this command will create all the files locally 

`jekyll new my_jekyll_site`

---
A new Jekyll site has been successfully created in '/Users/sujaykundu/Downloads/projects/my_jekyll_site'. The installation included:
1. Creating a new site with the default Jekyll theme (minima)
2. Installing all necessary dependencies through Bundler

You can now:
1. Navigate to the new site directory: `cd my_jekyll_site`
2. Start the Jekyll server: `bundle exec jekyll serve`

You can view your site by opening:
http://127.0.0.1:4000 in your web browser

Some key information about your running site:
- Source: /my_jekyll_site
- Destination: /my_jekyll_site/_site
- Server is running in auto-regeneration mode (will automatically update when you make changes)

You can:
1. Edit the site configuration in `_config.yml`
2. Add new posts in the `_posts` directory
3. Modify the content in `about.markdown` and `index.markdown`



```sh
bundle update github-pages
bundle install
```

### To start your local server
bundle exec jekyll serve

### To build your site
bundle exec jekyll build

### check local version of jekyll: 
`gem list jekyll`

*** LOCAL GEMS ***
jekyll (3.9.5)
jekyll-admin (0.11.1)
jekyll-avatar (0.8.0)
jekyll-coffeescript (1.2.2)
jekyll-commonmark (1.4.0)
jekyll-commonmark-ghpages (0.4.0)
jekyll-default-layout (0.1.5)
jekyll-feed (0.17.0)
jekyll-gist (1.5.0)
jekyll-github-metadata (2.16.1)
jekyll-include-cache (0.2.1)
jekyll-mentions (1.6.0)
jekyll-optional-front-matter (0.3.2)
jekyll-paginate (1.1.0)
jekyll-readme-index (0.3.0)
jekyll-redirect-from (0.16.0)
jekyll-relative-links (0.6.1)
jekyll-remote-theme (0.4.3)
jekyll-sass-converter (3.1.0, 3.0.0, 1.5.2)
jekyll-seo-tag (2.8.0)
jekyll-sitemap (1.4.0)
jekyll-swiss (1.0.0)
jekyll-theme-architect (0.2.0)
jekyll-theme-cayman (0.2.0)
jekyll-theme-dinky (0.2.0)
jekyll-theme-hacker (0.2.0)
jekyll-theme-leap-day (0.2.0)
jekyll-theme-merlot (0.2.0)
jekyll-theme-midnight (0.2.0)
jekyll-theme-minimal (0.2.0)
jekyll-theme-modernist (0.2.0)
jekyll-theme-primer (0.6.0)
jekyll-theme-slate (0.2.0)
jekyll-theme-tactile (0.2.0)
jekyll-theme-time-machine (0.2.0)
jekyll-titles-from-headings (0.5.3)
jekyll-watch (2.2.1)


## With Docker run local server (needs Docker installed locally)

if you don't want to install any ruby related environment follow this path


step 1. Clone pages-gem repository locally

`git clone https://github.com/github/pages-gem`


step 2. Run server

#### way 1:  using make 
step 2. Run make image from the root of the pages-gem directory to build an image which will be tagged as gh-pages

Start an instance of the server by running either:

`SITE=PATH_TO_YOUR_PROJECT make server` from the root of the gh-pages repository (where the Makefile resides)

eg. 

```s
cd pages-gem
make image 
SITE=/Users/sujaykundu/Downloads/projects/jekyller/my_jekyll_site make server
```

This will run the jekyll site locally using docker

```sh
test -d "/Users/sujaykundu/Downloads/projects/jekyller/my_jekyll_site" || \
		(echo -E "specify SITE e.g.: SITE=/path/to/site make server"; exit 1) && \
	docker run --rm -it \
		-p 4000:4000 \
		-u `id -u`:`id -g` \
		-v /Users/sujaykundu/Downloads/projects/pages-gem:/src/gh/pages-gem \
		-v `realpath /Users/sujaykundu/Downloads/projects/jekyller/my_jekyll_site`:/src/site \
		-w /src/site \
		gh-pages
Resolving dependencies...
Configuration file: /src/site/_config.yml
            Source: /src/site
       Destination: /src/site/_site
 Incremental build: disabled. Enable with --incremental
      Generating... 
       Jekyll Feed: Generating feed for posts
                    done in 0.23 seconds.
 Auto-regeneration: enabled for '/src/site'
    Server address: http://0.0.0.0:4000/
  Server running... press ctrl-c to stop.
  
```

### way 2: using github-pages gem cli

The gem comes with a github-pages cli that can be utilized, you need to run this command in pages-gem repo:

github-pages from the directory of the Jekyll site to be previewed when func.sh has been sourced into your terminal session.
`source contrib/func.sh`

```sh
github-pages <YOUR_JEKYLL_SITE_DIR_PATH>
```
replace `YOUR_JEKYLL_SITE_DIR_PATH` with the jekyll project path, eg.

`github pages /Users/sujaykundu/Downloads/projects/jekyller/my_jekyll_site`

This should run the serve the site:

```s
fatal: detected dubious ownership in repository at '/src/gh/pages-gem'
To add an exception for this directory, call:

	git config --global --add safe.directory /src/gh/pages-gem
Configuration file: /src/site/_config.yml
            Source: /src/site
       Destination: /src/site/_site
 Incremental build: disabled. Enable with --incremental
      Generating... 
       Jekyll Feed: Generating feed for posts
                    done in 0.184 seconds.
 Auto-regeneration: enabled for '/src/site'
    Server address: http://0.0.0.0:4000/
  Server running... press ctrl-c to stop.
  ```