# jekyller - Learn how to jekyll

Learn to build and host jekyll based sites using github actions and pages. Step-by-step instructions for begineers wanting to understand on how to use it.

### Jekyll
Jekyll is a static site generator. It takes text written in your favorite markup language and uses layouts to create a static website. You can tweak the site’s look and feel, URLs, the data displayed on the page, and more. 

For more info: [Jekyll Homepage](https://jekyllrb.com/)

Jekyll requires the following:

Ruby version 2.7.0 or higher
RubyGems
GCC and Make

### Github Pages

GitHub Pages is powered by Jekyll, a static site generator, meaning sites deployed using GitHub Pages are built using Jekyll

[Github Pages Gem](https://github.com/github/pages-gem)
[Githup Pages Dependencies versions](https://pages.github.com/versions/)

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
`gem install kramdown`

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
`bundle exec jekyll serve`

### To build your site
`bundle exec jekyll build`

### Liquid profiler
`bundle exec jekyll serve --profile`

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

```sh
github pages /Users/sujaykundu/Downloads/projects/jekyller/my_jekyll_site
```

This should run the serve the site:

```sh
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

  ### Yaml
#### If you need help with YAML syntax, here are some quick references for you:

 https://learn-the-web.algonquindesign.ca/topics/markdown-yaml-cheat-sheet/#yaml

 YAML - [Yaml](https://learnxinyminutes.com/yaml/)

  ### Markdown Configurations

 Kramdown - [Kramdown](https://kramdown.gettalong.org/)
 Kramdown Parser - [kramdown-parser-gfm](https://github.com/kramdown/parser-gfm)
 GFM - [Github Flavoured Markdown](https://github.github.com/gfm/)

 ### Syntax Highlighter  

Jekyll has built in support for syntax highlighting of over 100 languages thanks to Rouge. Rouge is the default highlighter in Jekyll 3 and above.

 Rouge - [Rouge](https://rouge.jneen.net/)
 Rouge Wiki - [List of supported languages and lexers](https://github.com/rouge-ruby/rouge/wiki/List-of-supported-languages-and-lexers)

 To render a code block with syntax highlighting, surround your code as follows:

```yaml
{% highlight ruby %}
def foo
  puts 'foo'
end
{% endhighlight %}
```

The argument to the highlight tag (ruby in the example above) is the language identifier. To find the appropriate identifier to use for the language you want to highlight, look for the “short name” on the Rouge wiki.

  ### Theme Configurations

  You can switch to supported themes list here  -  [pages.github.com/themes](https://pages.github.com/themes)

By default it comes with the theme [Minimal](https://pages-themes.github.io/minimal)

### Deploying the site to Github pages

[Creating a GitHub Pages site with Jekyll](https://docs.github.com/en/pages/setting-up-a-github-pages-site-with-jekyll/creating-a-github-pages-site-with-jekyll)


### Creating a custom jekyll site

#### To modify the layout, see https://jekyllrb.com/docs/themes/#overriding-theme-defaults

Create a new directory for your site 

create a `Gemfile` locally

Gemfile -> if jekyll doesnt install locally, you might need to create a Gemfile and do bundle install, to install all the gems defined in the Gemfile

Gemfile
```ruby
source "https://rubygems.org"

gem "github-pages", group: :jekyll_plugins

```

and install the gems :

```sh
bundle install
bundle exec jekyll -v # jekyll 3.10.0
```

create a new directory 'docs' to host our site

```sh
bundle exec new docs
cd docs 
bundle install
bundle exec jekyll serve  # to test the site locally
```
update _config.yml and posts in _posts directory

comment the theme gems in Gemfile 
comment the theme key in config.yml

create _layouts/default.html file add this :

```
 <!DOCTYPE html>
    <html>
    <head>
        <title>{{site.title}} - {{ page.title }}</title>
        <link rel="stylesheet" href="{{ '/style.css' | relative_url }}"> 
    </head>
    <body>
        <header>
            <!-- Header content -->
        </header>
        <main>
            {{ content }}
        </main>
        <footer>
            <!-- Footer content -->
        </footer>
    </body>
    </html>
```

#### Create a Homepage :

in the index.html file, update it to :
```
---
title: Homepage
layout: default
---
 
<div>
    <h1>Hello, world!</h1>
</div>

```
Now, if you run :

```sh
bundle exec jekyll serve --watch
```
You should see -> Hello, world!

#### Creating stylesheet:

create a new file style.css in assets/css/style.css

```css
h1 {
    color: #0077cc;
}
```

and update the path of stylesheet in /layouts/default.html to this:

```
       <link rel="stylesheet" href="{{ '/assets/css/style.css' | relative_url }}"> 
```

You should now see that all h1's got their color changed to blue #0077cc. Cool your styles are working.

### Liquid 

Jekyll uses liquid language - https://shopify.github.io/liquid

Using for loop:

You can loop a collection (about that below on how to create collections ) :

Suppose we have a collection of products in json format :

```json
[
  {
    "title": "hat",
    "price": "100"
  },
  {
    "title": "shirt",
    "price": "300"
  },
  {
    "title": "pant",
    "price": "800"
  }
]

```

```js
{% for product in collection.products %}
  {{ product.title }}
{% endfor %}
```
will display :

```js
hat shirt pant
```
You can learn more about iterations [here](https://shopify.github.io/liquid/tags/iteration/)

Using if else :

```js
{% for i in (1..5) %}
  {% if i == 4 %}
      {% break %}
  {% else %}
    {{ i }}
  {% endif %}
{% endfor %}
```

will display:

```js
1 2 3
```

forloop(object) has the following structure :

```json
{
  "first": true,
  "index": 1,
  "index0": 0,
  "last": false,
  "length": 4,
  "rindex": 3
}
```

Checking last index of for loop 

For example, if we want to add a , for every product but after the last product it should not show the comma (,) in that case you have iterate and find the last index and use unless.

```jsx
 {% for product in products %}
      {%- if product.length > 0 -%}
          {{ product.title }}{% unless forloop.last %} , {% endunless -%}
      {%- endif -%}
  {% endfor %}
```

will display: 

```js
hat, shirt, pant
```

#### Including templates

we can create templates by adding the files in _includes folder :

lets create a file called footer.html inside _includes folder:

```html

<h1> footer goes here </h1>


```
Now suppose we want to call the footer template from homepage (index.html)

In `index.html` you can call the template like this, and the footer will be processed :

```html
<div id="main">
  <h1> Homepage </h1>
</div>
<div id="footer">
  {% include footer.html %}
</div>
```

Including files relative to another filePermalink

{% include_relative somedir/footer.html %}

#### Adding Data Files (collections)

you can create data files with yml, json, csv and tsv format. create a directory _data 

for example:  List of members:

in yml format, In _data/members.yml: :

```yml
- name: Eric Mill
  github: konklone

- name: Parker Moore
  github: parkr

- name: Liu Fengyun
  github: liufengyun
  ```

in json format, In _data/members.json :

```json 
[
  {
    "name": "Eric Mill",
    "github": "konklone"
  },
  {
    "name": "Parker Moore",
    "github": "parkr"
  },
  {
    "name": "Liu Fengyun",
    "github": "liufengyun"
  }
]

in csv format, In _data/members.csv :

```csv
name,github
Eric Mill,konklone
Parker Moore,parkr
Liu Fengyun,liufengyun
```

in tsv format, In _data/members.tsv :

```tsv
name  github
Eric Mill konklone
Parker Moore parkr
Liu Fengyun liufengyun
```

This data can be accessed via site.data.members (notice that the file’s basename determines the variable name and therefore one should avoid having data files with the same basename but different extensions, in the same directory).

You can now render the list of members in a template:

```js
<ul>
{% for member in site.data.members %}
  <li>
    <a href="https://github.com/{{ member.github }}">
      {{ member.name }}
    </a>
  </li>
{% endfor %}
</ul>
```

You can also create subfolders 

Data files can also be placed in sub-folders of the _data folder. Each folder level will be added to a variable’s namespace. The example below shows how GitHub organizations could be defined separately in a file under the orgs folder:

In _data/orgs/jekyll.yml:

```yml
username: jekyll
name: Jekyll
members:
  - name: Tom Preston-Werner
    github: mojombo

  - name: Parker Moore
    github: parkr
````

In _data/orgs/doeorg.yml:

```yml
username: doeorg
name: Doe Org
members:
  - name: John Doe
    github: jdoe
```

The organizations can then be accessed via site.data.orgs, followed by the file name:

```js
<ul>
{% for org_hash in site.data.orgs %}
{% assign org = org_hash[1] %}
  <li>
    <a href="https://github.com/{{ org.username }}">
      {{ org.name }}
    </a>
    ({{ org.members | size }} members)
  </li>
{% endfor %}
</ul>
```




### Create a new github repo for the jekyll site

Once done, you can push to your github USERNAME.github.io repository. So create a new repo with USERNAME.github.io ->  Replace the USERNAME with your github username

Go the repo settings,

1. Change Default Branch -> gh-pages
2. Go to pages, enable pages and source -> Deploy from a branch, Branch -> gh-pages, Directory -> /docs. Press Save.

Now github will automatically build your jekyll site whenever you push to gh-pages branch.

### Pushing local changes to github

#### Creates a new branch, with no history or contents, called gh-pages, and switches to the gh-pages branch
`git checkout --orphan gh-pages`

#### Removes the contents from your default branch from the working directory
`git rm -rf .`


```sh
git add .
git commit -m 'Initial GitHub pages site with Jekyll'
git remote add origin https://github.com/USER/USERNAME.github.io.git
git push -u origin gh-pages
```
