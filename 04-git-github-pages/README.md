# git, GitHub, and GitHub Pages

## table of contents

* [what's git?](#whats-git)
  * [do I have to use the command line?](#do-i-have-to-use-the-command-line)
* [what's GitHub?](#whats-github)
  * [a note on account names](#a-note-on-account-names)
* [git with GitHub Desktop](#git-with-github-desktop)
* [git with the command line](#git-with-the-command-line)
  * [Setup](#setup)
  * [The Typical Workflow](#the-typical-workflow)
* [Deploying Your Website with GitHub Pages](#deploying-your-website-with-github-pages)
* [Licensing](#licensing)

## what's git?

[Git](http://git-scm.com/) (or `git`) is a "**version-control system**" (and in particular, a distributed one). In other words, it's a special type of software used to help us keep track of our code. We're not going to delve too deep into what that means, but for now, we'll note three core features it has:

* `git` helps back up your code - like Google Drive
* `git` lets you keep a history of all your changes you make to your code - like an undo button
* `git` lets you work on code with teammates, without interfering with each other's code - like (a better) Google Docs

Git is an invaluable skill to have if you do any sort of software development in the future. That being said, it *definitely* can be confusing! Here, we'll only focus on a very small subset of it, the bare minimum needed for our website.

### do I have to use the command line?

Nope! While `git` mostly does live on the command line, this workshop can be done with [GitHub Desktop](https://desktop.github.com), a desktop app that accomplishes the basic git tasks we do here!

*That being said*, familiarity with the command line and the `git` command is a big plus. If you plan on doing more coding in the future, it might be a good skill to pick up! But that doesn't have to start today if you're not comfortable.

## what's GitHub?

GitHub is *not* `git`, which is a common mistake! While `git` is a piece of softwared, GitHub is a product (and company) that *wraps around* `git` to make it easier to use and enhance some features. It's too much to list out at once, but we'll make use of:

* GitHub keeping copies of your code - no worries if you lose your computer!
* GitHub providing free domain hosting at `.github.io`
* GitHub has made a desktop client for `git` called GitHub Desktop!

There's also so many other cool features:

* GitHub makes collaborating with teammates easy!
* GitHub lets you automatically test your code with Actions
* GitHub lets you follow your friends and cool creators
* and much more!

Again, GitHub is very complicated, and don't worry at all about mastering it in a day! We'll walk you through the steps for your own website.

### a note on account names

When you make a GitHub account, we recommend thinking carefully about your account name; changing it down the line *is* a bit tricky, and if you're planning on using this professionally (many people do), you might want to think hard!

In addition, your account name determines the free domain GitHub gives you. if your account name is `geneblockme`, then your free GitHub domain will be `geneblockme.github.io`.

## git with GitHub Desktop

The process we'll use with GitHub Desktop is going to be:

1. make a repository on the GitHub website, called `YOUR_USERNAME.github.io`
2. "clone" it to your computer
3. add and commit your files in the portfolio
4. push your changes
5. see them in action :)

(Matt ran out of time to do this with screenshots for the day-of - please refer to [the GitHub Desktop Help page for now](https://docs.github.com/en/desktop). sorry!)

## git with the command line

*If you did the above steps with GitHub Desktop, feel free to skip this section!*

Here, we're assuming you're using a Unix-based shell (e.g. macOS, Linux, or Git Bash on Windows).

### Setup

Okay, how do we get started? We'll start by creating a folder, and then a git repository:

```sh
$ mkdir personal-portfolio
$ cd personal-portfolio
$ git init
...
```

`git init` creates an empty "git repository" in your folder.

Now, you make some changes. Here, we're making a random file, but feel free to move in your `index.html`.

```sh
$ echo "This is my personal portfolio" >> README.md
...
```

Now, we can check what `git` sees with `git status`:

```sh
$ git status
On branch main

No commits yet

Untracked files:
  (use "git add <file>..." to include in what will be committed)
    README.md

nothing added to commit but untracked files present (use "git add" to track)
```

This is an important distinction. Just because we've changed a file, doesn't mean it'll be updated just yet. To do that, we need to move it to staging, using `git add`; we're going to cheat and use the glob pattern `.`, which means all files (but we could've also done `git add README.md`):

```sh
$ git add .
$ git status
On branch main

No commits yet

Changes to be committed:
  (use "git rm --cached <file>..." to unstage)
    new file:   README.md
```

Great! Now we have files ready to be committed. Let's commit, with `git commit`

```sh
$ git commit -m "adding my README file"
...
```

The `-m` argument says to use the message from the command line, rather than entering a text editor.

Now, all that's left is to push our changes to GitHub. But wait! We haven't even told GitHub we're going to do something! So let's do that first!

Head to GitHub, and create a new repository. Two important things:

* make your repository name `YOUR_GITHUB_USERNAME.github.io` - you'll see why in a moment!
* don't "Initialize this repository with a README", add a `.gitignore`, or a license - we're going to import an existing repository!

Next, you'll get a prompt to "push an existing repository from the command line"; follow those commands:

```sh
$ git remote add origin https://github.com/YOUR_GITHUB_USERNAME/YOUR_GITHUB_USERNAME.github.io
...
```

Great, and now we're ready. We can finally run `git push`!

```sh
$ git push -u origin main
...
```

Now, if you head to your GitHub repository, you should see your changes pushed!

### The Typical Workflow

Now that we've got our repository all setup, here's what we do every time we want to make a new change:

* make your changes
* add all relevant files with `git add`
* use `git commit` to commit your changes locally
* run `git push` to send them to our origin (in this case, GitHub)
* double-check everything looks good on GitHub!

Note: we haven't talked about branches and pull requests yet. We'll do that for our next task, don't you worry!

## Deploying Your Website with GitHub Pages

**TL;DR: [read this guide](https://pages.github.com/).**

You want to show off your website to the world! The fancy word for being able to put your website on the internet is called *deploying* your website (or web application).

Your portfolio will probably be a *static website*, which means that there's no back-end, database, or dynamic process required to run your website - it's "static"! If your website is static, there are many different free options to deploy your website - which is an incentive to put as much into the frontend as possible!

One such option is [GitHub Pages](https://pages.github.com/), a static-site deployment provider made by GitHub! The biggest advantage: of GitHub Pages are

* It integrates *really easily* with GitHub, with no configuration required!
* You get a relatively clean URL (e.g. `krashanoff.github.io`) compared to other things like Netlify

In fact, if you followed the instructions above, it's already been configured for you! If you make a repository of the form `YOUR_GITHUB_USERNAME.github.io`, GitHub is pretty smart and automatically deploys the content of your repository to the domain `https://YOUR_GITHUB_USERNAME.github.io` (i.e. if you made a file `me.html`, then it would be at `https://YOUR_GITHUB_USERNAME.github.io/me.html`) - with no extra steps! How *extremely* convenient!!!

GitHub Pages does a bit more than that too - you can create a Pages site for each repository that you have, and use [Jekyll](https://jekyllrb.com) to super-charge your site! You can [review the documentation](https://pages.github.com/) for more information!

## Licensing

The contents of this repository are dual-licensed under the [MIT License](https://github.com/uclaacm/transfer-accel-portfolio-website-workshop/blob/main/LICENSE) and the [Creative Commons Attribution 4.0 License](https://creativecommons.org/licenses/by/4.0/); feel free to use whichever license suits your purpose better.

I'd love to hear if you found this helpful, or if you have any suggestions! Please send me an email at [matt@matthewwang.me](mailto:matt@matthewwang.me).
