# Introduction

Let's avoid this [humorous, yet sad situation from PhD
Comics](http://www.phdcomics.com/comics/archive.php?comicid=1531).

How might you solve this problem?

1. Maybe you are using sequentially numbered directories.
2. Maybe you are using track-changes.
3. Maybe you are using Google Docs.

## What is the problem with each of these approaches?

1. What if you overwrite something in the wrong directory?
2. What if you need to keep track of many files that depend on each other?
3. What if you want people to propose changes, but not make them?

## Enter version control

Version control lets you offload the work of keeping track of everything
related to a project, including documents, visualizations, and data.

You initialize it in a `directory` and then tell it when you want your
changes to be "permanent."

You can go back to a previous iteration at any time and can see exactly what
has changed between versions. The latter concept is called a "diff."

## For this workshop, we'll be using `git`

Git is a *distributed* version control system.

That means it can track, diff, and merge differences between the versions of a
file on your system and on *any other system on Earth*. This makes it a
powerful tool for collaborative work.


All of D-Lab's teaching materials and code are developed collaboratively with
`git`


## For this workshop, we'll also be using GitHub

GitHub is a website for keeping tabs on all the modified versions of your files
everywhere they appear.

GitHub makes it very easy to download, modify, and share code.

> Because of difficulties with CRAN, many R writers publish packages on GitHub
instead

## About me

My name is Juan Shishido, and I'm a graduate student at the School of
Information.

* I won't be able to answer all your questions
* No one will
* Because programming is one endless Google Search

At D-Lab, we call this last point "Rochelle's Law", after Rochelle Terman,
who once pronounced that the only difference between a clueless user and a tech
support guru is the amount of time spent Googling.


## Acknowledgments

This learning module borrows and adapts materials from the following
organizations and individuals. Thank you!

[Software Carpentry](https://github.com/swcarpentry/git-novice)
[Dav Clark](https://github.com/davclark/git-fundamentals)
