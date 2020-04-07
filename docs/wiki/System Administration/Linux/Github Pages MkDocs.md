# Github Pages MkDocs

## Create the repo
Generally easier to create it through GitHub and pull it down with `git clone`

## Create a `gh-pages` branch
```sh
git branch gh-pages
```
## Create MkDocs file structure
```sh
mkdocs new `filename`
```

## Do MkDocs things

* Create docs
* Edit the config file
* Change theming

## If you are going to make a domain/subdomain, do it now.

Move your CNAME file into the docs folder, so `mkdocs gh-deploy`
will keep it in your build.

## Commit it to master
```sh
git add .
git commit -m 'Update'
```

## MkDocs GitHub Pages Deploy
```sh
mkdocs gh-deploy
```

You should now have a static site at either your domain/subdomain
or at <GitHub Username>.github.io.