# Tracking

Okay, we have Git ready to go. Now, let's try using it!

## Initializing a repository

Let's start by making a new directory called `temp` and navigating to it.

```bash
$ mkdir temp
$ cd temp
```

To have Git start tracking what we're up to&mdash;that is, to initialize the
directory as a Git repository&mdash;do the following. 

```bash
$ git init
```

If you look in your directory, showing all files using `ls -a`, you'll see that
there is something called `.git`.

```bash
.    ..   .git
```

## Adding files

Cool! But this still isn't doing anything for us because this directory is
empty. So, let's create a file in our new directory and add some text to it.

```bash
$ echo "Data-intensive social science for all." > dlab.txt
```

To see the current state of the files in the repository

```bash
$ git status
On branch master

Initial commit

Untracked files:
  (use "git add <file>..." to include in what will be committed)

    dlab.txt

nothing added to commit but untracked files present (use "git add" to track)
```

Here, Git is telling you that there are local files that you haven't told it to
keep track of. While Git has a view into all the files in the directory, it
will only keep track of the files you tell it to.

Let's start tracking `dlab.txt`.

```bash
$ git add dlab.txt
```

Now, when we run `git status`, Git tells us that we've told it to keep track of
a new file. We call this being "staged."

```bash
On branch master

Initial commit

Changes to be committed:
  (use "git rm --cached <file>..." to unstage)

    new file:   dlab.txt

```

If this was a mistake, correct with the following

```bash
$ git rm --cached dlab.txt
```

We'll skip this step since we are interested in keeping track of it.

It's a good idea to add a `README.md` file to our directory so that we, and the
individuals who will collaborate with us, know the purpose of the project. For
now, we'll create the file but won't add anything to it.

```bash
$ touch README.md
```

Let's take a look at the current state of the directory.

```bash
$ git status
On branch master

Initial commit

Changes to be committed:
  (use "git rm --cached <file>..." to unstage)

    new file:   dlab.txt

Untracked files:
  (use "git add <file>..." to include in what will be committed)

    README.md

```

## Committing changes

Now we're ready to `commit` this file. Committing changes means making a
permanent record of the *current state* of your repository.

```bash
$ git commit
```

This will open your text editor and expect you to enter a message. You'll see
something like this:

```bash

# Please enter the commit message for your changes. Lines starting
# with '#' will be ignored, and an empty message aborts the commit.
# On branch master
#
# Initial commit
#
# Changes to be committed:
#   new file:   dlab.txt
#
# Untracked files:
#   README.md
#
```

Every commit needs a message to accompany it. It should be as brief as possible
while still describing the changes you made.

Making a whole bunch of changes and committing them all at once is a bad idea.
If you make many commit for many small changes, and one of those changes breaks
your code, you can *selectively undo* that change and fix the bug. If you make
only one commit, you'll have to re-do everything.

It takes a while to get a hang of this and there are many schools of thought on
what makes a good commit message (see
[here](http://chris.beams.io/posts/git-commit/#seven-rules), for example). A
useful approach is to imagine yourself or someone else reading the commit
messages at some future point in time. Think about a summary that might help
the reader understand the change. Another useful practice is to read other
people's commit messages.

Let's write "D-Lab motto" for this commit.

```bash
[master (root-commit) 7dab427] D-Lab motto
 1 file changed, 1 insertion(+)
 create mode 100644 dlab.txt
```

If you don't want your to have to use your text editor every time you make a
commit, you can use `-m`.

```bash
$ git commit -m "D-Lab motto"
```

In a repository, a file can exist in one of four states:

1. Untracked
2. Unmodified
3. Modified
4. Staged

![Explanatory graphic](https://git-scm.com/book/en/v2/book/02-git-basics/images/lifecycle.png)

We've already seen that `README.md` is untracked. Let's update `dlab.txt` and
then run `git status` again.

```bash
$ echo "350 Barrows Hall" >> dlab.txt
$ git status
On branch master
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git checkout -- <file>..." to discard changes in working directory)

    modified:   dlab.txt

Untracked files:
  (use "git add <file>..." to include in what will be committed)

    README.md

no changes added to commit (use "git add" and/or "git commit -a")
```

We can see that `dlab.txt` has been modified. To see what changed

```bash
$ git diff dlab.txt
diff --git a/dlab.txt b/dlab.txt
index 52277fd..1f82a5f 100644
--- a/dlab.txt
+++ b/dlab.txt
@@ -1 +1,2 @@
 Data-intensive social science for all.
+350 Barrows Hall
```

Since we know we'd like to stage (`add`) and commit this file, we can use

```bash
$ git commit -am "Added D-Lab's location"
[master f1446ab] Added D-Lab's location
 1 file changed, 1 insertion(+)
```

A note on `-a`: this automatically stages *all* files that have been modified
or deleted.

## Ignoring files

What if you have just put a bunch of files in your repo, that you want to add
all at once?

```bash
touch LICENSE CITATION script.R magic.py
```

You could write them all out in your add command, or you could use `git add -A`.

However, this will add *ALL THE THINGS* in your repo, which is probably
something you don't want.

* You don't want to clutter your tracked files with a bunch of temp or OS files
* You *especially* don't want to accidentally share any keys or credentials
files

Luckily, Git has a workaround for this called `.gitignore`.

```bash
$ echo "# Comment explaining what I'm ignoring
*.log" > .gitignore
```

Now, if we make a log file and try to add and commit with `-A`

```bash
$ touch test.log
$ git add -A
$ git status
On branch master
Changes to be committed:
  (use "git reset HEAD <file>..." to unstage)

    new file:   .gitignore
    new file:   CITATION
    new file:   LICENSE
    new file:   README.md
    new file:   magic.py
    new file:   script.R

```

Git ignores the log file&mdash;it doesn't even list it. Notice that `-A` also
added `README.md`.

## Acknowledgments

This learning module borrows and adapts materials from the following
organizations and individuals. Thank you!

[Software Carpentry](https://github.com/swcarpentry/git-novice)
[Dav Clark](https://github.com/davclark/git-fundamentals)
