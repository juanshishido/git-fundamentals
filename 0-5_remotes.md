## The Origin

While Git is useful to use locally, it is invaluable when there are lots of
people contributing to the same project. Generally, when there are lots of
people working on the same thing, it is good to have one authoritative source
of that thing. For this, we introduce the concept of a **remote** repository.
In Git, the default name for this is `origin`. This is typically not in your
local filesystem, though it can be. Rather, it's in a place where all of the
collaborators can read from it, even if they can't write to it.

## Cloning

When you `clone` a repository, Git automatically adds the source you cloned
from as the remote origin. Let's try.

```
$ git clone https://github.com/juanshishido/git-fundamentals.git
$ git remote -v
origin  https://github.com/juanshishido/git-fundamentals.git (fetch)
origin  https://github.com/juanshishido/git-fundamentals.git (push)
```

You can get information about that remote with

```
$ git remote show origin
* remote origin
  Fetch URL: https://github.com/juanshishido/git-fundamentals.git
  Push  URL: https://github.com/juanshishido/git-fundamentals.git
  HEAD branch: master
  Remote branches:
    gh-pages tracked
    master   tracked
  Local branch configured for 'git pull':
    master merges with remote master
  Local ref configured for 'git push':
    master pushes to master (up to date)
```

You can make changes to that repository, locally. However, unless you have
write permissions, you won't be able to push your changes to the remote. If you
tried, you might get something like

```
remote: Invalid username or password.
fatal: Authentication failed for 'https://github.com/juanshishido/git-fundamentals.git'
```

If you'd like to contribute to a project that you're not explicitly a part
of&mdash;that is, that you don't have write access to&mdash;you would *fork*
that repository.

## GitHub

**Enter the OctoCat**

![Here's lookin' at you, cat](https://octodex.github.com/images/privateinvestocat.jpg)

### Your first GitHub account

* Go to [https://github.com/join](https://github.com/join)
* Follow instructions!
* A free/student account is fine
* You'll want to use the same email address that you used for git locally
* Choose a strong password!

![But not this one](http://imgs.xkcd.com/comics/password_strength.png)

### Creating repos on GitHub

1. Go to your homepage
2. Press the `+` in the upper righthand corner
3. Select repository

GitHub initializes your repo for you, and can also create a LICENSE, README,
and .gitignore with common non-comitted files.

Let's create one for the work we've done on `temp`. Note: the remote GitHub
repository name *does not* have to match the name of your local version.

## Adding remotes

With `temp`, we first created the repository locally. We can add remoted to a
repository with `git remote add <alias> <url>`.

Now that you've created your remote repository on GitHub, let's add the remote
to our project. On the righthand side of your repository page, you'll see
"**HTTP** clone URL"&mdash;copy this. This is what you should use as the URL
in the command, below.

```
$ git remote add origin <url>
$ git remote -v
```

## Pull and Push

Now that you've added the remote, you'll want it to reflect the current state
of your repository.

```
$ git push origin master
```

By default, the main "branch" in any repository&mdash;remote or local&mdash;is
called "master." Now, if you look at your remote on GitHub, you'll see that it
reflects the current state&mdash;that is, it's up-to-date with 'origin/master'.

Now, let's edit `README.md`. Add whatever text you'd like. Remember that it's
currently not being tracked. Let's add it and commit. After you've edited the
file

```
$ git add README.md
$ git commit -m "<message>"
$ git push origin master
```

The nice thing about GitHub is that is takes the information in `README.md` and
renders and displays it on your repository page.

Whenever your collaborators make changes, you'll want to "pull" the changes
they've made to their files.

```
$ git pull origin master
```

It is very important to pull changes before you start modifying files.
