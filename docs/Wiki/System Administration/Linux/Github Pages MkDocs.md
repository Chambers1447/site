# Github Pages MkDocs

## Create the repo
Generally easier to create it through GitHub and pull it down with `git clone`

## Create a `gh-pages` branch
git branch gh-pages

## Create MkDocs file structure
mkdocs new `filename`

## Do MkDocs things

* Create docs
* Edit the config file
* Change theming

## If you are going to make a domain/subdomain, do it now.

Move your CNAME file into the docs folder, so `mkdocs gh-deploy`
will keep it in your build.

## Commit it to master

```
git add .
git commit -m 'Update'
```

## MkDocs GitHub Pages Deploy

```
mkdocs gh-deploy
```

You should now have a static site at either your domain/subdomain
or at <GitHub Username>.github.io.
