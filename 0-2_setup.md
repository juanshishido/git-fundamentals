# Setup

## On BCE

* You've already got it
* But, just for fun: `sudo apt-get install git`
* You should see

```
Reading package lists... done
Building dependency tree
Reading state information... done
git is already the newest version
```

* On a Debian system (like BCE), you install via `apt-get install`
* On a RHEL system, you install via `yumm install`

## On OS X

* Your system *might* already have Git installed
    * You can test this by opening a terminal and typing `git`
* If not, install Xcode from the App Store or with the following at the command
line: `xcode-select --install`
    * This installs the command line tools, a much smaller download

## On Windows

* You can try [Git for Windows](https://git-for-windows.github.io/)

## Other

* You can also download from [git-scm](https://git-scm.com/download/)

# Configuring Git to work with you

## You need to tell Git who you are

We do this by setting a couple of options in a file found in your home
directory.

```bash
$ git config --global user.name "Firstname Lastname"
$ git config --global user.email username@company.extension
```

Your name and email address is included in every change that you make, so it's
easy to keep track of who did what.

You might also want to change the default editor used by Git. For GNU nano

```bash
$ git config --global core.editor nano
```

Make sure everything was entered correctly by typing `git config --list`

```bash
user.name=<name>
user.email=<email>
core.editor=<editor>
```

## Acknowledgments

This learning module borrows and adapts materials from the following
organizations and individuals. Thank you!

[Software Carpentry](https://github.com/swcarpentry/git-novice)
[Dav Clark](https://github.com/davclark/git-fundamentals)
