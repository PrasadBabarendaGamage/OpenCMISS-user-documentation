[TOC]

#. Getting set up

It's a good idea to first go through the Git introduction at
http://gitref.org/ before reading this page. There's also a short
tutorial that was used for the ABI Summer Tutorial on Git at
https://abi-git-tutorial.readthedocs.org, which covers the basics and
some more advanced operations.

If you have to use Ubuntu 8.04 the ancient version of Git in the
repositories has issues working over https with GitHub so it's
recommended you compile the latest version of Git by following the steps
at [Compiling\_Git], or use the version of Git available in the
OpenCMISS extras svn repository.

If you want to make a change to OpenCMISS, you should first create an
account on GitHub (https://github.com) and go to
https://github.com/OpenCMISS/cm then click the fork button.

You now have a remote copy of the repository at
https://www.github.com/your_username/cm where you can backup your
changes and publish them so others can see what you're working on and
access your changes.

Now on your local machine, you need to first tell Git your name and
email address:

-  

   -  $ git config --global user.name "Your Real Name"\*\* #(real name,
      with spaces, not your GitHub user name)

-  

   -  $ git config --global user.email you@somedomain.com\*\* #(Your
      actual email address, not accountName@GitHub.com)

Just to be clear:

Please set user.name as \*\*YOUR REAL NAME\*\*, eg. "Joe Blog", \*\*NOT
your GitHub account name\*\*.

Please set user.email as \*\*YOUR ACTUAL EMAIL ADDRESS\*\*, eg.
joeblog@auckland.ac.nz.

If you don't have an editor specified with the EDITOR environment
variable, Git will open vim by default when you commit which can be
confusing so you might want to set your preferred editor:

-  

   -  $ git config --global core.editor "gedit"\*\*

To enable pretty colours in command outputs:

-  

   -  $ git config --global color.ui true\*\*

You can now clone your GitHub repository to the "cm" directory on your
local machine with:

-  

   -  $ git clone https://your_username@github.com/your_username/cm.git
      cm\*\*

or, if you have access through the git:port (and have added you SSH key
to your github profile) or problems over http you can try (slightly more
efficient):

-  

   -  $ git clone git@github.com:your\_username/cm.git cm\*\*

Move into the cm directory

-  

   -  $ cd cm\*\*

Your Git repository keeps a list of remote repositories with an alias
for each one. By default your GitHub repository will be called "origin"
as it is the repository you originally cloned. We'll add the central
OpenCMISS repository and call it "upstream". This only needs to be done
once for each repository and is important to do so that you can keep up
to date with changes in the central repository:

-  

   -  $ git remote add upstream https://github.com/OpenCMISS/cm.git**

This process should be repeated for the OpenCMISS examples repository at
https://github.com/OpenCMISS/examples and the CellML repository at
https://github.com/OpenCMISS/cellml, although if you will not be making
changes to one or more of these repositories you can clone them directly
from https://github.com/OpenCMISS.

#. Making changes

When you want to work on a new feature you should first discuss your
planned changes with the OpenCMISS technical or project leaders and by
creating a tracker item.

Two possible workflows are presented, a simple workflow for those new to
Git, and a branching workflow for those comfortable with Git usage.

#. 

   #. Simple workflow

If you want to use Git in a similar way to Subversion you can just work
on your master branch.

To see what you've changed:

-  

   -  $ git status\*\*

-  

   -  $ git diff\*\*

To make a commit, use:

-  

   -  $ git commit -a\*\*

See the [commit messages](#Commit\_messages) section for how messages
should be formatted.

To publish your changes to your remote repository:

-  

   -  $ git push origin master\*\*

#. 

   #. Keeping up to date

It's important to often pull in changes from the central repository to
make sure your work stays up to date.

First make sure all your changes are committed, then to get changes from
upstream (similar to doing an svn update):

-  

   -  $ git pull upstream master\*\*

If your master branch has not diverged from the central master branch,
Git will do what is called a "fast-forward" merge and just add the new
commits on linearly.

If you have made some commits in your master branch Git will try to
automatically merge your branch with the central repository's master
branch. If there are no conflicts git will create a merge commit itself
and you don't have to do anything more.

If there are merge conflicts when you pull from upstream you will have
to fix these and then make a commit. Running \*\*git status\*\* will
show which files have conflicts, and you can run \*\*git mergetool
path/to/file\*\* to use a graphical tool to resolve the conflict, or
just edit the file with your preferred editor and the conflict will be
indicated with conflict markers. When you have resolved the conflicts in
a file you can run \*\*git add path/to/file\*\* to say that the
conflicts have been resolved.

When all conflicts are resolved you can then create a merge commit:

-  

   -  $ git commit\*\*

And finally push the merge to your remote repository:

-  

   -  $ git push origin master\*\*

#. 

   #. Branching workflow

When you've got the OK and are ready to start work on a new feature or
fix, create a branch from the master branch and then use the checkout
command to checkout the new branch into your working directory.

-  

   -  $ git branch new\_feature master\*\*

-  

   -  $ git checkout new\_feature\*\*

A shortcut that combines these two commands is \*\*git checkout -b
new\_feature master\*\*, and if you're already on the master branch you
can just use \*\*git checkout -b new\_feature\*\*.

Now work on your changes while making commits. You should aim to break
work up into small commits so it's obvious to others how work has
progressed, and split separate features or fixes into separate branches.

Git has an index or staging area where you add changes from your working
directory before committing them. To add a changed file to the index
use:

-  

   -  $ git add path/to/changed/file\*\*

You can also select only some changes in a file to add to the index with
the --patch or -p option.

Running \*\*git status\*\* will show you the files that are changed in
your working directory and in the index.

To view what has changed in your working directory but isn't in the
index, use \*\*git diff\*\*. To view the changes that have been added to
the index, use \*\*git diff --cached\*\*

Running \*\*git commit\*\* will open your text editor for you to enter a
commit message before making a commit from the changes that have been
added to the index. See the [commit messages](#Commit\_messages) section
for how messages should be formatted.

If you prefer to bypass the index and want to make a commit like in
Subversion by committing all changes to tracked files, you can pass the
-a or --all option:

-  

   -  $ git commit -a\*\*

Push the changes on your new\_feature branch to your repository on
GitHub with:

-  

   -  $ git push origin new\_feature\*\*

Or to push all branches:

-  

   -  $ git push --all origin\*\*

The fetch command will get new changes from a remote repository.

The pull command does a fetch and then merges the specified branch.

-  

   -  $ git pull origin old\_feature\*\*

To merge the changes from upstream into your local master branch, use:

-  

   -  $ git checkout master\*\*

-  

   -  $ git pull upstream master\*\*

Merging the master branch changes into your feature branch:

-  

   -  $ git checkout new\_feature\*\*

-  

   -  $ git merge master\*\*

#. 

   #. Commit messages

Commit messages should consist of a short summary line, followed by a
blank line and then further explanation including the relevant tracker
item. All lines should be less than about 80 characters. Many Git tools
are designed to work with commit messages formatted in this way and will
use just the subject line in many places. Messages with one long line or
without a blank line after the first line will look bad in a lot of
tools.

#. 

   #. Getting changes into the central repository

When your code is ready to be merged into the central repository make
sure all changes are pulled in from upstream and then push the branch to
your remote repository.

-  

   -  $ git checkout master\*\*

-  

   -  $ git pull upstream master\*\*

If you're working on the master branch you can then just run:

-  

   -  $ git push origin master\*\*

Otherwise you also need to merge the changes from master into your
feature branch:

-  

   -  $ git checkout new\_feature\*\*

-  

   -  $ git merge master\*\*

-  

   -  $ git push origin new\_feature\*\*

Then go to https://github.com/your_username/cm and click the "Pull
Request" button. This brings up a page where you can select the branch
you want merged and describe the changes you want pulled in.

You then need to find someone to review your changes and assign them to
the tracker item for your feature or fix. They can make comments on your
code in the pull request. If any changes are needed you can make more
commits on the feature branch and they will be added to the pull
request, there is no need to create a new pull request. Once the
reviewer has approved your changes they will add a comment on the
tracker item saying so and your commits will be merged into the master
branch.

Once you're finished with a branch you can delete it with:

-  

   -  $ git branch -d new\_feature\*\*

You can delete branches on your remote repository by providing a blank
source commit to the push command:

-  

   -  $ git push origin :new\_feature\*\*

This syntax may look a little strange at first but it makes more sense
once you know that \*\*git push origin feature\_branch\*\* is the same
as running \*\*git push origin feature\_branch:feature\_branch\*\*,
where the colon separates the source and destination references.

#. Reviewing code and pushing to the central repository

If you want to review someone else's changes you can either just view
the changes on the GitHub web interface or check out their branch on
your machine. For commits without any merge conflicts, GitHub can apply
a pull request automatically.

To get their code you first need add their GitHub repository to your
list of remote repositories if it isn't already:

-  

   -  $ git remote add username https://github.com/username/cm.git**

Fetch their changes:

-  

   -  $ git fetch username\*\*

See what they changed:

-  

   -  $ git diff master...username/new\_feature\*\* #(using "a..b" will
      diff commits a and b, "a...b" shows a diff of b with the common
      ancestor of a and b)

Checkout their branch:

-  

   -  $ git checkout username/new\_feature\*\*

You can also create a new local branch that tracks their remote branch
with:

-  

   -  $ git checkout -b new\_feature username/new\_feature\*\*

The branches don't have to have the same name but it usually makes sense
that they do.

If you then want to merge the changes into the central repository:

-  

   -  $ git checkout master\*\*

-  

   -  $ git merge username/new\_feature\*\*

Now push to the central repository:

-  

   -  $ git push upstream master\*\*

#. Other useful commands

-  

   -  git help [command\_name]\*\* shows an explanation of any git
      command and its options.

-  

   -  git log\*\* shows history

-  

   -  gitk\*\* will open a gui for visualising history, you can pass the
      --all option to see all branches

-  

   -  git stash\*\* allows you to stash local changes before switching
      branches if you're not ready to commit them, and then you can
      later reapply them on the same or another branch.

-  

   -  git commit --amend\*\* will let you change the previous commit if
      you haven't yet pushed it.

-  

   -  git bisect\*\* will help you track down commits that introduced a
      bug.

-  

   -  git show [commit\_id]\*\* will show you what changed in a commit

-  

   -  git difftool\*\* instead of \*\*git diff\*\* to use a graphical
      application such as meld or kdiff3 to view a diff.

-  

   -  git rebase\*\* will let you rearrange and modify commits.

-  

   -  git reset\*\* is for making your branch HEAD point to another
      commit (useful for undoing commits), and can also be used to
      remove changes from your index.

You can use aliases for common commands, for example:

-  

   -  $ git config --global alias.diffc "diff --cached"\*\*

-  

   -  $ git config --global alias.lol "log --graph --decorate --oneline
      --abbrev-commit"\*\*

You can use a graphical merge tool to help resolve merge conflicts. To
specify the program to use, run:

-  

   -  $ git config --global merge.tool meld\*\*

where meld could be replaced by kdiff3 or any tool listed in \*\*git
help mergetool\*\*. Then to resolve a merge conflict in a file you can
run:

-  

   -  $ git mergetool path/to/file\*\*

You can add the current branch name to your bash prompt using the
\_\_git\_ps1 function.

#. Git resources

Git has very good help that can be accessed with "git help" and "git
help [command]"

Some other useful online resources:

| `` * ``\ ```http://tbaggery.com/2008/04/19/a-note-about-git-commit-messages.html`` <http://tbaggery.com/2008/04/19/a-note-about-git-commit-messages.html>`__\ `` Commit message formatting``
| `` * ``\ ```http://gitref.org/`` <http://gitref.org/>`__\ `` A short Git tutorial``
| `` * ``\ ```http://help.github.com/`` <http://help.github.com/>`__\ `` GitHub's help site``
| `` * ``\ ```http://progit.org/book/`` <http://progit.org/book/>`__\ `` ProGit book``
| `` * ``\ ```http://vimeo.com/17118008/`` <http://vimeo.com/17118008/>`__\ `` video walkthrough (~1hr) of git basics by one of the developers of Github``
| `` * ``\ ```http://help.github.com/git-cheat-sheets/`` <http://help.github.com/git-cheat-sheets/>`__\ `` printable cheat sheets for quick reference``

See also:

`` * [Notes comparing DVCSs made before switching to Git](Distributed_version_control_systems)``
