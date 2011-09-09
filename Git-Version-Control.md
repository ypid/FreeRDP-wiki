# Installation

## Linux

Most Linux distributions have a git package, often named "git" or "git-core". On Ubuntu, the package name is git-core:

[Ubuntu Git](https://help.ubuntu.com/community/Git)

You can install it on Ubuntu like this:

sudo apt-get install git-core

## Mac OS X

The command-line git client is available in macports:

[macports git](http://trac.macports.org/browser/trunk/dports/devel/git-core/Portfile)

If you already have macports installed, you can install it like this:

sudo port install git-core

If you do not have macports installed, you may want to use git-osx-installer instead:

[git-osx-installer](http://code.google.com/p/git-osx-installer/)

## Windows

If you already have cygwin installed, it might be easier to install git on cygwin:

[cygwin git](http://cygwin.com/cgi-bin2/package-cat.cgi?file=git/git-1.7.4-1&grep=git-core)

An easy to install command-line git client for Windows is msysgit:

[msysgit](http://code.google.com/p/msysgit/)

However, if you intend to use git frequently on Windows, you may want to take a look at Git Extensions, a very nice git gui with full native Windows integration:

[git extensions](https://sourceforge.net/projects/gitextensions/)

# Documentation

Git being a popular distributed version control system (DVCS), there are a lot of good documentation written about it. The GitHub help page contains a very nice list of available resources and references:\\ 

[Help.GitHub](http://help.github.com/)

Otherwise, there is "Pro Git", an excellent free book:

[Pro Git](http://progit.org/)

And finally, the git user's manual:

[Git User's Manual](http://www.kernel.org/pub/software/scm/git/docs/user-manual.html)

# SSH Keys

One nice feature of git is that you can configure ssh keys such that you do not have to enter your developer password every time you want to interact with the server. On most systems, if you already have generated ssh keys, they will appear within your ~/.ssh directory:

`awake@workstation:~> ls -l ~/.ssh`
`total 12`
`-rw------- 1 awake users 1675 2011-02-03 21:17 id_rsa`
`-rw-r--r-- 1 awake users  399 2011-02-03 21:17 id_rsa.pub`
`-rw-r--r-- 1 awake users 3094 2011-02-13 10:16 known_hosts`

If you do not have ssh keys (id_rsa and id_rsa.pub files), generate them using "ssh-keygen -t rsa":

`awake@workstation:~> ssh-keygen -t rsa`
`Generating public/private rsa key pair.`
`Enter file in which to save the key (/home/awake/.ssh/id_rsa): `
`Enter passphrase (empty for no passphrase): `
`Enter same passphrase again: `
`Your identification has been saved in /home/awake/.ssh/id_rsa.`
`Your public key has been saved in /home/awake/.ssh/id_rsa.pub.`
`The key fingerprint is:`
`db:71:38:e7:c2:5e:b8:9f:01:25:ee:52:d6:59:d2:2a awake@workstation`
`The key's randomart image is:`
`+--[ RSA 2048]----+`
`|                 |`
`|             .   |`
`|          . o o  |`
`|         . = =   |`
`|        S E *    |`
`|         B X     |`
`|        o * +    |`
`|         o + o   |`
`|          o.o    |`
`+-----------------+`

ssh keys consist of a pair of public and private keys. The private key (~/.ssh/id_rsa), like the name says, is the one which you keep for yourself. The public key (~/.ssh/id_rsa.pub) is the one which you should add to your sourceforge.net account so that it can be used for authentication with git over ssh.

To add ssh keys to your github account, first log in, go to the "Account Settings" page, and click "SSH Public Keys" on the left. Click on "Add another public key".

Get your public ssh key using "cat ~/.ssh/id_rsa.pub":

`awake@workstation:~> cat ~/.ssh/id_rsa.pub `
`ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQC/T7KPdDwsFKA+tUf2JbknDUuW6OLFYGOc1/I8N+NVfAE3BRaMYgmQVOpBg74TWQRcynCuLV7r4doOP8YalvZI4oGHlI2TIqOE0wG2GP0Hm4Atxoy+6yKZOZcK5eRk0mXBBdNPxgYZ1xX1tb9Usm04NCkPsOegVo08TW6TX6mO1ZArkZ3m97i5vUC8FX/uhqoPj7MNiSTr7P6cwGk8IatM+25wVAcmBVJSbsj6YYQVC3U0y76Lp51f20yFQvq2eyTBol6eweOFwI0yFpXWx1To1ABRpHdpuZtXRrPJVWq30lituwdv6iCFXNpitWbTKnkt6jr7xeP08crG5LlPcZlb awake@workstation`

Copy everything, starting from "ssh-rsa" up to "awake@workstation" in the above example, and paste it in the given text box. Click update, wait a few minutes, and you should now be able to use git without having to enter a password from the computer using that ssh key.

Please note that if you use more than one computer, you will need to set up ssh keys for all of them. If you have more than one ssh key, you need to paste them one per line in the above text box.

# Usage

The url for the public read-only git repository is the following:

`git://github.com/FreeRDP/FreeRDP.git`

Developers with read/write access use the following url instead:

`git@github.com:FreeRDP/FreeRDP.git`

## Cloning

In order to fetch the sources from git, you will need to **clone** a repository. If you are used to subversion terminology, this is the rough equivalent of doing an "svn checkout":

For most people, this will be done using:
`git clone git://github.com/FreeRDP/FreeRDP.git`

For developers with read/write access, this will be done using:
`git clone git@github.com:FreeRDP/FreeRDP.git`

Here is what it should look like:

`awake@workstation:~/git> git clone git://github.com/FreeRDP/FreeRDP.git`
`Initialized empty Git repository in /home/awake/git/freerdp/.git/`
`remote: Counting objects: 7304, done.`
`remote: Compressing objects: 100% (5132/5132), done.`
`remote: Total 7304 (delta 3734), reused 5403 (delta 2154)`
`Receiving objects: 100% (7304/7304), 5.72 MiB | 918 KiB/s, done.`
`Resolving deltas: 100% (3734/3734), done.`

## Fetching

A simple "git fetch" sometimes has to be done in order to ensure that your local repository is in sync with the remote repository, especially if new remote branches or tags have been created in the meantime:

`git fetch`

## Status

"git status" is probably one of the git commands which you will use often to know your current status. After a fresh git clone, the status should normally look like this:

`awake@workstation:~/git/freerdp> git status`
`# On branch master`
`nothing to commit (working directory clean)`

If you add a new file in the repository that is not tracked by the version control yet, it will be listed by git status:

`awake@workstation:~/git/freerdp> git status`
`# On branch master`
`# Untracked files:`
`#   (use "git add <file>..." to include in what will be committed)`
`#`
`#       libfreerdp/new_file.c`
`nothing added to commit but untracked files present (use "git add" to track)`

If you modify a file that is tracked by the version control, it will also be listed by git status:

`awake@workstation:~/git/freerdp> git status`
`# On branch master`
`# Changed but not updated:`
`#   (use "git add <file>..." to update what will be committed)`
`#   (use "git checkout -- <file>..." to discard changes in working directory)`
`#`
`#       modified:   libfreerdp/freerdp.c`
`#`
`no changes added to commit (use "git add" and/or "git commit -a")`

## Config

Before committing stuff, developers will need to properly configure their git repository with their developer information. You can list the local git configuration with "git config --list":

`awake@workstation:~/git/freerdp> git config --list`
`user.name=Your Username`
`user.email=username@email.com`
`core.repositoryformatversion=0`
`core.filemode=true`
`core.bare=false`
`core.logallrefupdates=true`
`remote.origin.fetch=+refs/heads/*:refs/remotes/origin/*`
`remote.origin.url=git@github.com:FreeRDP/FreeRDP.git`
`branch.master.remote=origin`
`branch.master.merge=refs/heads/master`

If you are a regular git user, and use the same git configuration for multiple git repositories, you may want to use the "--global" option to all your "git config" commands, such that you edit global settings instead of local settings:

`awake@workstation:~/git/freerdp> git config --global --list`
`user.name=Your Username`
`user.email=username@email.com`

You will need to edit two variables, "user.name", and "user.email", before committing anything:

`awake@workstation:~/git/freerdp> git config --global user.name "Your Username"`
`awake@workstation:~/git/freerdp> git config --global user.email "username@email.com"`

You can check that the changes were accepted by doing a "git config --list"

## Branching

Once you have cloned the repository, change directory to it:

`awake@workstation:~/git> cd freerdp`

You can check which branch you are currently on with "git branch"

`awake@workstation:~/git/freerdp> git branch`
`* master`

The current branch is marked with a star '*'. We currently only have one local branch.

You can list all branches, local or remote, using "git branch -a"

`awake@workstation:~/git/freerdp> git branch -a`
`* master`
`  remotes/origin/HEAD -> origin/master`
`  remotes/origin/integration`
`  remotes/origin/maint`
`  remotes/origin/master`
`  remotes/origin/pulse`

Alternatively, you can list only remote branches using "git branch -r"

`awake@workstation:~/git/freerdp> git branch -r`
`  origin/HEAD -> origin/master`
`  origin/integration`
`  origin/maint`
`  origin/master`
`  origin/pulse`

Now, let's say you want to try the sources that are located on the "origin/pulse" remote branch, because you are eager to try PulseAudio support. In order to do so, you need to create a new local branch that tracks that particular remote branch:

`awake@workstation:~/git/freerdp> git branch --track pulse origin/pulse`
`Branch pulse set up to track remote branch pulse from origin.`

This should have successfully created a new local branch that matches the remote "pulse" branch. You can now see the local "pulse" branch in your local branches:

`awake@workstation:~/git/freerdp> git branch`
`* master`
`  pulse`

However, you will notice in the above output that the star is still besides "master", and not "pulse", meaning that we are still looking at the master branch. To switch branches, use "git checkout <branch_name>"

`awake@workstation:~/git/freerdp> git checkout pulse`
`Switched to branch 'pulse'`

And then verify that you are looking at the correct branch:

`awake@workstation:~/git/freerdp> git branch`
`  master`
`* pulse`

Creating a new branch in git is trivial. First, switch to the branch from which you want to base your new branch:

`awake@workstation:~/git/freerdp> git checkout master`
`Switched to branch 'master'`

Then create the new branch, which we will call "sample", and switch to it:

`awake@workstation:~/git/freerdp> git branch sample`
`awake@workstation:~/git/freerdp> git branch`
`* master`
`  sample`
`awake@workstation:~/git/freerdp> git checkout sample`
`Switched to branch 'sample'`
`awake@workstation:~/git/freerdp> git branch`
`  master`
`* sample`

Now, for the purpose of this sample, we will create a new file, create a new version from it, and push the new branch to the remote branch of the same name:

`awake@workstation:~/git/freerdp> echo "test" > test.txt`
`awake@workstation:~/git/freerdp> git status`
`# On branch sample`
`# Untracked files:`
`#   (use "git add <file>..." to include in what will be committed)`
`#`
`#       test.txt`
`nothing added to commit but untracked files present (use "git add" to track)`
`awake@workstation:~/git/freerdp> git add test.txt`
`awake@workstation:~/git/freerdp> git status`
`# On branch sample`
`# Changes to be committed:`
`#   (use "git reset HEAD <file>..." to unstage)`
`#`
`#       new file:   test.txt`
`#`
`awake@workstation:~/git/freerdp> git commit -m "test comment for git wiki article"`
`[sample 4e83e74] test comment for git wiki article`
` 1 files changed, 1 insertions(+), 0 deletions(-)`
` create mode 100644 test.txt`
`awake@workstation:~/git/freerdp> git push origin sample`
`Counting objects: 4, done.`
`Delta compression using up to 8 threads.`
`Compressing objects: 100% (2/2), done.`
`Writing objects: 100% (3/3), 305 bytes, done.`
`Total 3 (delta 1), reused 0 (delta 0)`
`To git@github.com:FreeRDP/FreeRDP.git`
` * [new branch]      sample -> sample`

Branches are inexpensive and easy to use, so you can use them whenever you feel like it. However, just make sure you know how to delete them ;)

To delete a local branch, you must first switch to another branch, since you cannot delete the current branch:

`awake@workstation:~/git/freerdp> git checkout master`
`Switched to branch 'master'`
`awake@workstation:~/git/freerdp> git branch -D sample`
`Deleted branch sample (was 4e83e74).`

To above command "git branch -D <branch_name>" will only delete the local branch, which means the remote branch remains unaffected. To delete the remote branch as well, do the following:

`awake@workstation:~/git/freerdp> git push origin :sample`
`To git@github.com:FreeRDP/FreeRDP.git`
` - [deleted]         sample`

The difference in the above command is that in order to delete a branch, you do a regular "git push" command, except that you precede the remote branch name by a semi-colon ':'.

## Pulling

"pulling" in git terminology means pulling the latest version of a remote branch onto a local branch. For instance, if you are currently on the master branch, and want to pull the latest version:

`awake@workstation:~/git/freerdp> git branch`
`* master`
`  pulse`
`awake@workstation:~/git/freerdp> git pull origin master`
`From git@github.com:FreeRDP/FreeRDP.git`
` * branch            master     -> FETCH_HEAD`
`Already up-to-date.`

Alternatively, if you are working on a branch other than master, you will want to pull from the branch which you are tracking:

`awake@workstation:~/git/freerdp> git branch`
`  master`
`* pulse`
`awake@workstation:~/git/freerdp> git pull origin pulse`
`From git@github.com:FreeRDP/FreeRDP.git`
` * branch            pulse      -> FETCH_HEAD`
`Already up-to-date.`

You may begin to notice the pattern in the git pull command:

`git pull origin <remote_branch>`

The git pull command, without any additional parameters, will always pull the remote branch specified directly onto the current branch, so make sure you know which branch you are currently looking at.

git pull can also be used to merge branches (it can call git merge for you). Let's say you want to merge the latest version of master with the current version from the "pulse" branch. You can do so by switching to your local "pulse" branch, and doing a "git pull origin master" on it:

`awake@workstation:~/git/freerdp> git pull origin master`
`From git@github.com:FreeRDP/FreeRDP.git`
` * branch            master     -> FETCH_HEAD`
`Updating 25785e8..f26bbbb`
`Fast-forward`
` LICENSE                                     |  202 +++`
` X11/xf_types.h                              |    1 +`
` X11/xf_win.c                                |   60 +-`
` X11/xfreerdp.c                              |  119 +-`
`...`
` vnc/x11stubs.h                              |   33 -`
` win/libfreerdp.vcproj                       |   24 +`
` win/wfreerdp/wfreerdp.cpp                   |   46 +-`
` 167 files changed, 7256 insertions(+), 17709 deletions(-)`
` create mode 100644 LICENSE`
` create mode 100644 cunit/test_credssp.c`
` create mode 100644 cunit/test_credssp.h`
`...`
` delete mode 100644 vnc/x11stubs.c`
` delete mode 100644 vnc/x11stubs.h`

If automatic merging was successful, you can now push the merged branch onto the remote pulse branch:

`git push origin pulse`

Sometimes, automatic git merging fails. Files that could not be merged will be listed differently by "git status". In order to resolve the merge, you need to manually inspect each of those files and finish merging by yourself. Once the merging is done, you need to do a "git add" on each of those files, followed by a git commit.

## Committing

In git terminology, the action of committing results in a new version being created. This is a bit different from subversion where the term means pushing changes to the remote repository. With git, committing (creating a new version) is an action separate from pushing that new version to a remote repository.

For the purpose of this sample, let's say that I am working on the master branch, and I have a fix for dfbfreerdp ready to submitted:

`awake@workstation:~/git/freerdp> git branch`
`  integration`
`* master`
`awake@workstation:~/git/freerdp> git status`
`# On branch master`
`# Changed but not updated:`
`#   (use "git add <file>..." to update what will be committed)`
`#   (use "git checkout -- <file>..." to discard changes in working directory)`
`#`
`#	modified:   dfb/dfbfreerdp.c`
`#`
`no changes added to commit (use "git add" and/or "git commit -a")`

The first step is to add all the files that I want to include in the new version I want to create, using "git add":

`awake@workstation:~/git/freerdp> git add dfb/dfbfreerdp.c`
`awake@workstation:~/git/freerdp> git status`
`# On branch master`
`# Changes to be committed:`
`#   (use "git reset HEAD <file>..." to unstage)`
`#`
`#	modified:   dfb/dfbfreerdp.c`
`#`

Other commands such as "git mv" or "git rm" exist to prepare changes that should be included in a commit. "git status" lists changes that are going to be committed, and detected changes that are not included.

When you are done preparing changes to be included in the new version, you can use "git commit" with the "-m" option to add a comment describing the changes made:

`awake@workstation:~/git/freerdp> git commit -m "updating dfbfreerdp command line options for NLA"`
`[master a8b907f] updating dfbfreerdp command line options for NLA`
` 1 files changed, 97 insertions(+), 0 deletions(-)`

Once the new version is created, we want to push it from the local master branch to the remote master branch:

`awake@workstation:~/git/freerdp> git push origin master`
`To git@github.com:FreeRDP/FreeRDP.git`
` ! [rejected]        master -> master (non-fast-forward)`
`error: failed to push some refs to 'git@github.com:FreeRDP/FreeRDP.git'`
`To prevent you from losing history, non-fast-forward updates were rejected`
`Merge the remote changes before pushing again.  See the 'Note about`
`fast-forwards' section of 'git push --help' for details.`

In the above example, pushing failed because a new version was pushed on master in the meantime. This means we should first merge our new version with the latest version from the remote master branch, and attempt pushing again. Pulling solves that problem 99% of the time:

`awake@workstation:~/git/freerdp> git pull origin master`
`remote: Counting objects: 51, done.`
`remote: Compressing objects: 100% (27/27), done.`
`remote: Total 27 (delta 20), reused 0 (delta 0)`
`Unpacking objects: 100% (27/27), done.`
`From git@github.com:FreeRDP/FreeRDP.git`
` * branch            master     -> FETCH_HEAD`
`Removing channels/rdpsnd/rdpsnd_pulse.c`
`Merge made by recursive.`
` channels/rdpsnd/alsa/rdpsnd_alsa.c   |  158 +++++++---`
` channels/rdpsnd/pulse/Makefile.am    |   23 ++`
` channels/rdpsnd/pulse/rdpsnd_pulse.c |  573 ++++++++++++++++++++++++++++++++++`
` channels/rdpsnd/rdpsnd_dsp.c         |  147 +++++++++-`
` channels/rdpsnd/rdpsnd_dsp.h         |   10 +-`
` channels/rdpsnd/rdpsnd_main.c        |   58 +++-`
` channels/rdpsnd/rdpsnd_pulse.c       |  102 ------`
` channels/rdpsnd/rdpsnd_types.h       |   19 +-`
` configure.ac                         |   17 +`
` doc/xfreerdp.1                       |   26 ++-`
` 10 files changed, 959 insertions(+), 174 deletions(-)`
` create mode 100644 channels/rdpsnd/pulse/Makefile.am`
` create mode 100644 channels/rdpsnd/pulse/rdpsnd_pulse.c`
` delete mode 100644 channels/rdpsnd/rdpsnd_pulse.c`

In this case, automatic merging was successful, so we can attempt pushing again:

`awake@workstation:~/git/freerdp> git push origin master`
`Counting objects: 10, done.`
`Delta compression using up to 8 threads.`
`Compressing objects: 100% (6/6), done.`
`Writing objects: 100% (6/6), 1.65 KiB, done.`
`Total 6 (delta 4), reused 0 (delta 0)`
`To git@github.com:FreeRDP/FreeRDP.git`
`   6f7eb2a..e80996f  master -> master`

## Pushing

Pushing requires write access, so it is only available to developers.

Let's say you are developing straight on master, and want to push the changes from your local branch to the remote master branch:

`awake@workstation:~/git/freerdp> git branch`
`* master`
`  pulse`
`awake@workstation:~/git/freerdp> git push origin master`

Alternatively, if you are developing on a separate branch, you will need to pay careful attention to push to your own remote branch:

`awake@workstation:~/git/freerdp> git branch`
`  master`
`* pulse`
`awake@workstation:~/git/freerdp> git push origin pulse`

If you develop on your own branch, you probably do not want to push straight on master! Be careful, don't use "git push origin master" blindly all the time.