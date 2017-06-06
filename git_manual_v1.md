Git Manual
==========

Here's a diagram of the basic workflow:

![Workflow Overview](/Users/programmer/Projects/dev_ops/overview.png)

Creating a new website
----------------------

1. Go to the central repository.
2. Create a new folder. Name it something intelligently.
3. Run `git init --bare` to build the site's repository.
4. Now anyone can run `git clone programmer@sltrepo.byu.edu:/path/to/repo` to get a copy.

### Example ###

1. Go to the central repository.

	Pretend our repository is stored under the home directory of `sltrepo.byu.edu`.
	
		$ ssh programmer@sltrepo.byu.edu
		$ cd repos/

2. Create a new folder.

		$ mkdir my_new_site
		$ cd my_new_site/

3. Run `git init --bare` to build the site's repository.

		$ git init --bare

4. Go to your desktop and clone.

		$ cd Projects/
		$ git clone programmer@sltrepo.byu.edu:repos/my_new_site/


Git concepts
------------

A Git repository has multiple "branches". These are like separate copies of the project. There is always one branch called `master`. There can be any number of other branches.

When you start working on a website, you will need to clone the repository. Create a branch with your name in it. This is your copy of the project.

When someone has made some changes on a branch that you want to incorporate, use `git merge <branchname>` to pull their changes. Most of the time the changes will take place automatically. If you have edited the same section of code, Git will ask you to resolve the conflicts. (Type `git status` to see where the conflicts are.) Once you are done resolving conflicts, you can invoke `git push` to send the merged code back into the central repository.

The repository lives on a separate machine from the development servers. Use `Filezilla` or `rsync` to push your code from your desktop to the server. Using a tool like `make` can automate this process for you. To see a sample Makefile (the thing `make` needs to automate builds) checkout the _Supply Tracker_ project. Currently, the project lives on `ayeaye`.

Desktop Setup
-------------

1. Make sure you have Git installed.

2. Make a place for your repos to live.
    Use a folder called `Projects/` on your desktop machine.

3. Setup username and email.
	Do this so we know who committed what. You can set the username and password like this: (you don't have to be in a particular folder)
	
		$ git config --global user.name "Your Name"
		$ git config --global user.email "youremail@provider.com"

4. Clone the site.
	 Run `git clone programmer@sltrepo.byu.edu:repos/new_site/`

Practices
---------

 - At the end of every day, **COMMIT AND PUSH YOUR CODE!!**
     We don't have backups of the desktop machines. 
 - Commit often.
     Even if all you've done is added a few lines of code, commit. You should be committing code multiple times a day. You don't necessarily have to push.
 - Keep branch `master` clean.
	 Don't merge into `master` unless you have had your code reviewed, and are sure it is bug-free. We want to keep `master` deployable at all times.

Workflow
--------

#### Solo/Fixing an old project ####



#### Collaboration ####

Each programmer should have their own development branch for active development. Make sure your name is in the branch so we know who is working on what. For example, if Arthur and Ashton were to be working on the same project, they would do this:

(Ashton's side)

    $ git clone programmer@sltrepo.byu.edu:repos/supplytracker/
        Cloning into 'supplytracker'...
        remote: Counting objects: 1629, done.
        remote: Compressing objects: 100% (1347/1347), done.
        remote: Total 1629 (delta 956), reused 631 (delta 229)
        Receiving objects: 100% (1629/1629), 1.68 MiB | 0 bytes/s, done.
        Resolving deltas: 100% (956/956), done.
    $ cd supplytracker/
    $ git branch ashton_new_feature
    $ git checkout ashton_new_feature
        Switched to branch 'ashton_new_feature'

(Arthur's side)

    $ git clone programmer@sltrepo.byu.edu:repos/supplytracker/
        Cloning into 'supplytracker'...
        remote: Counting objects: 1629, done.
        remote: Compressing objects: 100% (1347/1347), done.
        remote: Total 1629 (delta 956), reused 631 (delta 229)
        Receiving objects: 100% (1629/1629), 1.68 MiB | 0 bytes/s, done.
        Resolving deltas: 100% (956/956), done.
    $ cd supplytracker/
    $ git branch arthur_some_other_feature
    $ git checkout arthur_some_other_feature
        Switched to branch 'arthur_some_other_feature'

Okay, now Ashton and Arthur each have their own branch. Now, when Ashton changes something, he can commit and push his branch to the server. Arthur can do the same.

When Arthur has finished a particular feature that Ashton wants to work with, Ashton can do something like this from *his* branch:

(Ashton's side)

	$ git pull arthur_some_other_feature
	$ git merge arthur_some_other_feature



At the end of the day, Arthur and Ashton should commit and push their changes:

	$ git add -A
	$ git commit -m "notes for tomorrow"
	$ git push

These will push changes to the programmer's personal branches. As soon as they are ready to pass off a feature, they should review each other's code, then merge with `master` and push:

	$ git checkout master
	$ git merge arthur_some_other_feature
	$ git push


Further Reading
---------------

Here are some resources to help you with using Git:

 - [Comparing Workflows](https://www.atlassian.com/git/tutorials/comparing-workflows#feature-branch-workflow)

     We're using something like the "feature branch workflow". This website has some other helpful tutorials.

 - If you're new to Git, there's a lovely tutorial on Git's main page [here](https://try.github.io/levels/1/challenges/1).
