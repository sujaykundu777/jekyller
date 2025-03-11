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



### jekyll gems:
`gem install jekyll -v 3.9.3`
`gem install bundler`
`gem pristine --all`


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

# To start your local server
bundle exec jekyll serve

# To build your site
bundle exec jekyll build