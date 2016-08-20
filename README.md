
<h1 align="center">My Blog</h1>

## How to fork it

### Prerequisite


 - [Chrome](https://www.google.com/chrome/) - use the installer
 - [Jekyll](https://jekyllrb.com/) - ```$ gem install jekyll```
 - [NodeJS](https://nodejs.org/en/download/) - use the installer.


Versions I used : node 5.11.1, npm 3.8.6, gulp 3.9.1, jekyll 3.1.6, ruby 2.3.0

### Dev mode

```shell

$ git clone https://github.com/bdavidxyz/protheme2
$ cd protheme2
$ npm install
$ $(npm bin)/gulp
 # ta-da ! the browser launches itself,
 # and will rebuild and live-reload each time you
 # change a CSS, JS, or HTML file
```

### Production mode

The website will deploy on branch gh-pages, so create a new repository <your_repo_name> in Github, and add the remote in your project like this :


```shell

# be sure you start from a fresh GitHub state
$ rm -rf .git
$ git init
$ git add . && git commit -m 'initial commit'
$ git remote add origin git@github.com:<your_github_name>/<your_repo_name>.git
# in config.prod.yml, set baseurl to <your_repo_name>
$ git push -u origin master

# I suppose you've already run npm install ?
$ gulp deploy
# ta-da ! your super optimized website
# can be see at  https://<your_github_name>/<your_repo_name>/
```

## Credits

Design mainly inspired from Nicolas Hery's blog.