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

