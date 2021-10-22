About Citric-OS:
================
![CitricOS Image](https://github.com/Citric-OS/android_manifest/blob/slime/assets/citric-banner.png)

```bash
Citric OS is a custom skin based upon AOSP. It targets being unique, essential and stable; providing a pleasing user experience.
```
-----------------------------------------------------------------------------

How to build Citric-OS for your device
==============================================

Build Environment
-----------------

- Tested and Working on any version of Ubuntu - 14.04, 14.10, 15.04, 16.04, 18.04, 20.04 (64-bit)
- Any other distribution based of the Ubuntu Distro such as Lubuntu, Xubuntu and etc.
- Any form of Terminal
- Decent hardware (minimum of at least a quad core CPU and 16 GB of RAM)
- A storage unit of any kind (We recommend utilizing SSDs as Mechanical HDDs slow down the build proccess drastically and the minimum storage size is 70GB. Having more will be useful with CCache[More on that later])
- Required Packages should have been installed

Preparing Build Environment
-------------------------------
Before we build, we need to prepare the environment to be able to build.

We recommend to use [@akhilnarang](https://github.com/akhilnarang)'s [scripts](https://github.com/akhilnarang/scripts)

```bash
     git clone https://github.com/akhilnarang/scripts
     cd scripts && bash setup/android_build_env.sh
```

Downloading Citric-OS Source Codes
-------------------------------

Create build folder

```bash
     mkdir ~/citric
     cd ~/citric
```

To get started with the building process, you'll need to get familiar with [Git and Repo](http://source.android.com/source/using-repo.html).

To initialize your local repository, use a command like this:


```bash
     repo init -u https://github.com/Citric-OS/android_manifest.git -b slime
```

To save time, space and internet data, sync with --depth=1 :

```bash
     repo init --depth=1 -u https://github.com/Citric-OS/android_manifest.git -b slime
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
     source build/envsetup.sh
     lunch citric_<devicecodename>-userdebug
     m citric
```

-----------------------------------------------------------------------------


Credits:
=======

* [**LineageOS/Cyanogenmod**](https://github.com/LineageOS)
* [**ABC ROM**](https://github.com/ezio84)
* [**Pixel Experience**](https://github.com/PixelExperience)
* [**DirtyUnicorns**](https://github.com/DirtyUnicorns)
* [**AOSPA**](https://github.com/aospa/)
* [**Nitrogen Project**](https://github.com/nitrogen-project)
* [**Extended-UI**](https://github.com/Extended-UI)
* [**OmniROM**](https://github.com/omnirom/)
* [**BlissRoms**](https://github.com/BlissRoms)
* [**POSP**](https://github.com/PotatoProject)
* [**Evolution-X**](https://github.com/Evolution-X)
* [**Syberia-Project**](https://github.com/syberia-project)
* [**Project Awaken**](https://github.com/Project-Awaken)
* [**Project Fluid**](https://github.com/Project-Fluid)
* [**WaveOS**](https://github.com/wave-project)
* [**@akhilnarang**](https://github.com/akhilnarang) for prepare environment script.

----------------------------------------------------------------------------------------------------------
