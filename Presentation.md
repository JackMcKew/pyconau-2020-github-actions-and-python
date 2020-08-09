# GitHub Actions & Python

PyconAU 2020 - Jack McKew

* What are GitHub Actions?
* Why use them?
* How to set them up?

---

## Quick Note

This talk is open source & built with GitHub Actions at: <https://github.com/JackMcKew/pyconau-2020-github-actions-and-python>

---

## Who am I

I'm Jack McKew, I absolutely love solving problems, especially with Python! 🐍

I write a weekly blog on software, technology and more over at [jackmckew.dev](https://jackmckew.dev/).

You can reach me on:

* Twitter: [@jac_mcq](https://twitter.com/jac_mcq)
* LinkedIn: [jack-mckew](https://www.linkedin.com/in/jack-mckew/)
* GitHub: [@JackMcKew](https://github.com/JackMcKew)

---

## Projects I work on

I'm the creator & maintainer of open source packages such as:

* [Pandas_Alive](https://github.com/JackMcKew/pandas_alive).
* [awesome-python-bytes](https://github.com/JackMcKew/awesome-python-bytes).
* Numerous GitHub Actions:
    * [pyinstaller-action-windows](https://github.com/JackMcKew/pyinstaller-action-windows)
    * [pyinstaller-action-linux](https://github.com/JackMcKew/pyinstaller-action-linux)
    * [python-interrogate-check](https://github.com/JackMcKew/python-interrogate-check)

---

## What are GitHub Actions

GitHub Actions are free-to-use, plug & play blocks of continuous integration / continuous delivery (CI/CD).

> CI/CD allows us to automate building, testing and deployment of applications.

---

## GitHub Action Marketplace

Find pre-made blocks of CI/CD to plug & play!

> <https://github.com/marketplace?type=actions>

---

![GitHub Marketplace](img/github-marketplace.png)

---

## Why should you use them

If you can automate something, you definitely should.

<iframe src='https://gfycat.com/ifr/AchingOptimisticAlabamamapturtle' frameborder='0' scrolling='no' width=100% height='500'></iframe><p> <a href="https://gfycat.com/achingoptimisticalabamamapturtle">via Gfycat</a></p>

---

### What I use GitHub Actions for

This talk!!

And also...

* Testing!
* Building/managing documentation
* Syncing examples with working code
* Checking all external links are valid in documentation
* Checking docstring coverage (with [interrogate](https://pypi.org/project/interrogate/))
* Packaging Python code as an executable

---

## But how do I set them up

All's needed is a `my-action.yml` file in `.github/workflows`

``` yaml
name: Build & Publish Presentation with reveal-md

on: push

jobs:
  release:
    name: Build & Publish
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v1

      - name: Install dependencies & Build Presentation
        run: |
          sudo npm install -g reveal-md --unsafe-perm
          sudo reveal-md Presentation.md --static _site --highlight-theme github
      - name: Deploy 🚀
        uses: JamesIves/github-pages-deploy-action@releases/v3
        with:
          ACCESS_TOKEN: ${{ secrets.ACCESS_TOKEN }}
          BRANCH: gh-pages # The branch the action should deploy to.
          FOLDER: _site # The folder the action should deploy.
```

---

### Let's break it down

``` yaml
name: Build & Publish Presentation with reveal-md

on: push
```
<!-- .element: class="fragment" data-fragment-index="1" -->

``` yaml
jobs:
  release:
    name: Build & Publish
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v1
```
<!-- .element: class="fragment" data-fragment-index="2" -->

``` yaml
      - name: Install dependencies & Build Presentation
        run: |
          sudo npm install -g reveal-md --unsafe-perm
          sudo reveal-md Presentation.md --static _site --highlight-theme github
```
<!-- .element: class="fragment" data-fragment-index="3" -->

``` yaml
      - name: Deploy 🚀
        uses: JamesIves/github-pages-deploy-action@releases/v3
        with:
          ACCESS_TOKEN: ${{ secrets.ACCESS_TOKEN }}
          BRANCH: gh-pages # The branch the action should deploy to.
          FOLDER: _site # The folder the action should deploy.
```
<!-- .element: class="fragment" data-fragment-index="4" -->

---
