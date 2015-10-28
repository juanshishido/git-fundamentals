# Undoing changes

## Log

Git takes care of all these things for you behind the scenes (even branching
and merging, which we'll talk about later), but sometimes you need to know when
and by whom changes were made. To see the commit logs

```
$ git log
commit f1446abe740b2872dc384eb656d300622dd2220f
Author: juanshishido <juanshishido@cal.berkeley.edu>
Date:   Tue Oct 27 22:11:27 2015 -0700

    Added D-Lab's location

commit 7dab4278f3bed2e14860b1bd4676fe5225d58b2a
Author: juanshishido <juanshishido@cal.berkeley.edu>
Date:   Tue Oct 27 21:45:13 2015 -0700

    D-Lab motto
```

This shows the entire history of this repository in reverse chronological order.

To see the the diffs on the files you've committed, you can use `git log -p`.
However, because our commit messages give us a pretty good idea of what we did,
we don't necessarily need to use the `-p` flag.

## Checkout

Let's imagine that we changed our minds about having the D-Lab's location in
`dlab.txt`. We could make the changes manually, but Git provides a better way
for us to revert to a previous state.

The `git checkout` command lets us either return the *entire* directory to a
previous state or access a previous version of a particular file. (The checkout
command is also useful for switching branches.)

In our example, because we've only committed a single file, these will
essentially be the same operation.

If you recall, we have several files (e.g., `magic.py` and `script.R`) in the
staging area. Let's commit those changes before we use the checkout command and
look at the log.

```
$ git commit -m 'Adding empty citation, license, Python, and R files'
$ git log
commit e63d4f2e2366088f34b671e6e0d99e0105ffcdfe
Author: juanshishido <juanshishido@cal.berkeley.edu>
Date:   Tue Oct 27 23:27:50 2015 -0700

    Adding empty citation, license, Python, and R files

commit f1446abe740b2872dc384eb656d300622dd2220f
Author: juanshishido <juanshishido@cal.berkeley.edu>
Date:   Tue Oct 27 22:11:27 2015 -0700

    Added D-Lab's location

commit 7dab4278f3bed2e14860b1bd4676fe5225d58b2a
Author: juanshishido <juanshishido@cal.berkeley.edu>
Date:   Tue Oct 27 21:45:13 2015 -0700

    D-Lab motto
```

Now, we can either checkout a commit or a particular file. Because we're only
interested in reverting `dlab.txt`, let's checkout that file. Before we do,
let's print the file's contents. After checking it out, let's print the file
contents again.

```
$ cat dlab.txt
Data-intensive social science for all.
350 Barrows Hall
$ git checkout 7dab4278f3bed2e14860b1bd4676fe5225d58b2a dlab.txt
$ cat dlab.txt
Data-intensive social science for all.
```

When checking out a file, `git checkout` takes the commit hash and file name as
arguments. The long set of alpanumeric characters is the hash and its the way
that Git references and identifies commits. When you do this on your own
computer, the hash will be different. I've provided the entire 40-character
hash. In reality, all Git needs is enough characters to uniquely identify the
commit.

Notice that the second time we call `cat dlab.txt`, the "350 Barrows Hall" part
is gone. This is the only file that's been reverted to a previous state and all
of our other files are still there.

```
$ ls
CITATION  LICENSE   README.md dlab.txt  magic.py  script.R  test.log
```
