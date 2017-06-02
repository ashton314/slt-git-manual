SLT Dev Ops
===========

This is a draft for some things we can change to help our programmers work better. Specifically, these changes will help programmers learn to write better code, make our development cycles safer and more stable, and make our software more robust and flexible.

These tools will help:

 - Git
 - MAMP (for old PHP sites)
 - Laravel (for new sites)

In addition to these tools, we will need some simple policies in place on how we *use* these tools.

Git
---

### What is Git? ###

Git is a computer program. It's a simple binary like `diff` or `grep` or `find`. Git is not a website. _GitHub_ is a website, and it uses Git to work. We can use Git independent of GitHub.

### What does one do with Git? ###

Git lets you maintain control of different versions of your programs. It also lets you colaborate with multiple programmers and still keep your code from getting messy. It lets you see every change you've made to your software and when. (And much more!)

Installing Git is as easy as installing any other package. Git is extremely well maintained, and has legendary documentation.

Setting up a Git repository is super easy. Let's say we designate `ayeaye` as our central repository. This is all we would need to do:

	$ mkdir repos

So far we only have a directory. What happens when we want to make a new website? Well, we just do this:

	$ cd repos; mkdir new_site; cd new_site
	$ git init --bare
	Initialized empty Git repository in /home/programmer/repos/new_site/

Now we have a repository for the site. This will function as the "single source of truth" for the site.

Let's say a progammer wants to start working on the site. On their desktop computer, they *clone* the repository:

	$ cd Projects
	$ git clone programmer@ayeaye.byu.edu:repos/new_site/
	Cloning into 'new_site'...
	warning: You appear to have cloned an empty repository.
	Checking connectivity... done.

Now we can made some edits, add files, etc. Once we are done, we first use `git add` to specify what files we want to *commit*, then we use `git commit` to finalize the changes:

    $ git add index.html js/basics.js
	$ git commit -m "added basic headers, etc. on landing page"
	[master (root-commit) b7c2e7a] added basic headers, etc. on landing page
	2 files changed, 0 insertions(+), 0 deletions(-)
	create mode 100644 index.html
	create mode 100644 js/basics.js

We can do this `git add` and `git commit` process as often as we want. Ideally, this is done after every atomic change: adding a function, a new `<div>` tag, etc. The 

### Why? ###

 - debugging
 - collaboration
 - experimenting
 - saftey
 - consistency between dev/prod
 - knowledge out of the heads of the programmers and into records

### What sort of policies should we adopt? ###

 - code reviews
 - `master` is always deployable
 - 

### Git concepts in detail ###

