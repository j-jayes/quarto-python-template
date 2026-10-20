# Python + Quarto template

A starting point for repos that mix Python with Quarto, especially reveal.js slides published on GitHub Pages.

The only thing in here is a `.gitignore`. It is GitHub's Python template, unchanged, with a Quarto block at the end.

## Why

GitHub's Python `.gitignore` ignores `dist/`, `lib/` and `build/` anywhere in the repo. Quarto copies reveal.js into a `revealjs/dist/` folder, under `site_libs/` for a project or `<name>_files/libs/` for a single document. Git quietly skips it, GitHub Pages never gets it, and the slides show up as unstyled text.

The Quarto block re-includes everything under `site_libs/` and `*_files/`. It comes last because in a `.gitignore` the last matching rule wins. Python build output at any level is still ignored.

The longer story is on the blog: [Why your reveal.js slides have no styling on GitHub Pages](https://blog.jonathanjayes.com/posts/2026-05-15-quarto-revealjs-github-pages-gitignore).

## Use it

New repo:

```bash
gh repo create my-project --template j-jayes/quarto-python-template --public --clone
```

Or click **Use this template** on GitHub.

Existing repo:

```bash
curl -fsSL https://raw.githubusercontent.com/j-jayes/quarto-python-template/main/.gitignore -o .gitignore
git add -A && git status   # the missing revealjs/dist files should now show up
```

If the slides were already published broken, re-render and commit the files that now appear.
