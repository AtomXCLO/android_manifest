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
./rom-build.sh [DEVICE] [args]
```

-----------------------------------------------------------------------------
