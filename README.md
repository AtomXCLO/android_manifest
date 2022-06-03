About The AtomX Project:
========================
![The AtomX Project Image](https://github.com/Atom-X-Devs/.github/blob/main/banner.jpg)

```bash
AtomX is a custom skin based upon sources from CodeLinaro. It targets being unique, essential and stable; providing a pleasing user experience.
```
-----------------------------------------------------------------------------

How to build AtomX for your device
==================================

Build Environment
-----------------

- Tested and works on any version of Ubuntu - 16.04, 18.04, 20.04, 21.04, 22.04 (64-bit)
- Any other distribution based of the Ubuntu Distro such as Lubuntu, Xubuntu and etc.
- Any form of Terminal
- Decent hardware (minimum of at least a quad core CPU and 16 GB of RAM)
- A storage unit of any kind (We recommend utilizing SSDs as Mechanical HDDs slow down the build proccess drastically and the minimum storage size is 70GB. Having more will be useful with CCache[More on that later])
- Required Packages should have been installed

Preparing Build Environment
---------------------------
Before we build, we need to prepare the environment to be able to build.

We recommend to use [@akhilnarang](https://github.com/akhilnarang)'s [scripts](https://github.com/akhilnarang/scripts)

```bash
git clone https://github.com/akhilnarang/scripts
cd scripts && bash setup/android_build_env.sh
```

Downloading AtomX Source Codes
------------------------------

Create build folder

```bash
mkdir ~/atomx
cd ~/atomx
```

To get started with the building process, you'll need to get familiar with [Git and Repo](http://source.android.com/source/using-repo.html).

To initialize your local repository, use a command like this:


```bash
repo init -u https://github.com/AtomXCLO/android_manifest.git -b sc-v2
```

To save time, space and internet data, sync with `--depth=1` :

```bash
repo init --depth=1 -u https://github.com/AtomXCLO/android_manifest.git -b sc-v2
```

Then to sync up
---------------

```bash
repo sync -c --force-sync --no-tags --no-clone-bundle -j$(nproc --all) --optimized-fetch --prune
```

Finally to build
----------------

From root directory of Project, perform following commands in terminal

```bash
Usage: ./rom-build.sh <device> [options]

Options:
  -h, --help            Display this help message
  -c, --clean           Wipe the tree before building
  -i, --installclean    Dirty build - Use 'installclean'
  -r, --repo-sync       Sync before building
  -t, --build-type      Specify build type
  -j, --jobs            Specify jobs/threads to use
  -m, --module          Build a specific module
  -s, --sign-keys       Specify path to sign key mappings
  -p, --pwfile          Specify path to sign key password file
  -b, --backup-unsigned Store a copy of unsignied package along with signed
  -d, --delta           Generate a delta ota from the specified target_files zip
  -z, --imgzip          Generate fastboot flashable image zip from signed target_files
```

Submitting Patches
==================

We're open source and patches are always welcome!

You can see the status of all patches at [Gerrit Code Review](https://review.atomx-devs.org/).

Following the standard workflow
-------------------------------

```bash
# Start by going to the root of the source tree
$ cd WORKSPACE

# Create a new branch on the specific project you are going to work on
# For example, `repo start fix-clock AtomXCLO/android_frameworks_base`
$ repo start BRANCH AtomXCLO/PROJECT
# You can also use the project path in place of the project name.
# The PROJECT_DIR is the portion after the android_ prefix on
# the AtomXCLO Github.  For example, android_frameworks_base translates
# into the directory frameworks/base.
# This applies to all repo commands that reference projects.
$ repo start BRANCH PROJECT_DIR

# Go inside the project you are working on
$ cd PROJECT_DIR

# Make your changes
...

# Commit all your changes
$ git add -A
$ git commit -a -s

# Upload your changes
$ cd WORKSPACE
$ repo upload AtomXCLO/PROJECT
# or
$ repo upload PROJECT_DIR
```

Using plain git to upload
-------------------------

```bash
# Go inside the project you are working on
$ cd PROJECT_DIR

# Make your changes
...

# Commit all your changes
$ git add -A
$ git commit -a -s

# Upload your changes
$ git push ssh://USERNAME@review.atomx-devs.org:29418/AtomXCLO/PROJECT HEAD:refs/for/sc-v2
```

Extra commands for Gerrit
-------------------------

```bash
# If you desire to upload a change as private use the below command
$ git push ssh://USERNAME@review.atomx-devs.org:29418/AtomXCLO/PROJECT HEAD:refs/for/sc-v2%private

# If you desire to upload a change as W.I.P(Work in Progress) use the below command
$ git push ssh://USERNAME@review.atomx-devs.org:29418/AtomXCLO/PROJECT HEAD:refs/for/sc-v2%wip

# After that, if you want to make the commit public you can use the UI tools on AtomXCLO Gerrit website, or use the below command
$ git push ssh://USERNAME@review.atomx-devs.org:29418/AtomXCLO/PROJECT HEAD:refs/for/sc-v2%remove-private

# If you want to unset the W.I.P status on your commit, you can use UI tools on AtomXCLO Gerrit website, or use the below command
$ git push ssh://USERNAME@review.atomx-devs.org:29418/AtomXCLO/PROJECT HEAD:refs/for/sc-v2%ready
```

Making additional changes
-------------------------

If you are going to make more changes, you just have to repeat the steps (except for `repo start`
which you should not repeat) while using `git commit --amend` instead of `git commit -a -s` so that
you avoid having multiple commits for this single change. Gerrit will then recognize these changes
as a new patch set and figure out everything for you when you upload.

Squashing multiple commits
--------------------------

Your patches should be single commits. If you have multiple commits laying around, squash them by
running `git rebase -i HEAD~<commit-count>` before uploading.

Writing good commit messages
----------------------------

You will be asked a commit message when you run `git commit`. Writing a good commit message is
often hard, but it is also essential as these messages will stay around with your changes and
will be seen by others when looking back at the project history.

A few general pointers to keep in mind when writing the commit message are that you should use
imperative as it matches the style used by the `git merge` and `git revert` commands (that means
"Fix bug" is preferred over "Fixes bug", "Fixed bug" and others) and that you should write the
first line of the commit message as a summary of the commit. It should always be capitalized and
followed by an empty line. You might optionally include the project name at the start and try to
keep it to 50 characters when possible as it is used in various logs, including "one line" logs.

-----------------------------------------------------------------------------
