# site
Repository for my site.

Made and maintained with `mkdocs` and `mkdocs-material`.

To clone and use my site:

## Dependencies:

* `mkdocs`
* `mkdocs-material`
* `mkdocs-awesome-plugin`

## Installation:

Install the dependencies.

```sh
python3 -m pip install mkdocs --user
python3 -m pip install mkdocs-material --user
python3 -m pip install mkdocs-awesome-pages-plugin --user
```

Clone the repository.

```sh
git clone https://github.com/DirWalk/site.git
```

Serve it locally with:

```sh
mkdocs serve
```

Or you can also push it to GitHub pages:

```sh
mkdocs gh-deploy
```

There is already a `gh-pages` repository created, switch to that branch to check it with:

```sh
git checkout gh-pages
```

You should change the CNAME file, or remove it if you're using the GitHub pages supplied name.