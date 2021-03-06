# Source Install V 0.6-3 (DEV)

Build and install from sources is possible.  However, the source build for AOMP is complex for several reasons.
- Many repos are required.  The clone_aomp.sh script ensures you have all repos and the correct branch.
- Requires that Cuda SDK 10 is installed for NVIDIA GPUs. ROCm does not need to be installed for AOMP.
- It is a bootstrapped build. The built and installed LLVM compiler is used to build library components.
- Additional package dependencies are required that are not required when installing the AOMP package.

Building AOMP from source requires these dependencies that can be resolved on an ubuntu system with apt-get.

```
   sudo apt-get install cmake g++-5 g++ pkg-config libpci-dev libnuma-dev libelf-dev libffi-dev git python libopenmpi-dev
```
## AOMP Verify and Install Linux Support

Please verify you have the proper software installed as AOMP needs certain support for Linux to function properly, such as the KFD driver for AMD GPUs and CUDA for nvptx. Click [LINUXSUPPORT](LINUXSUPPORT.md) for more information.

## Clone and Build AOMP

```
   cd $HOME ; mkdir -p git/aomp ; cd git/aomp
   git clone https://github.com/rocm-developer-tools/aomp
   cd $HOME/git/aomp/aomp/bin
```

<b>Choose a Build Version (Development or Release)</b>
The development version is the next version to be released.  It is possible that the development version is broken due to regressions that often occur during development.  If instead, you want to build from the sources of a previous release such as 0.6-2 that is possible as well.

<b>For the Development Branch:</b>
```
   git checkout master 
```

<b>For the Release Branch:</b>
```
   git checkout rel_0.6-2
   git pull
```
<b>Clone and Build:</b>
```
   ./clone_aomp.sh
   ./build_aomp.sh
```
Depending on your system, the last two commands could take a very long time. For more information, please refer to the AOMP developers README file located [HERE](bin/README.md).

You only need to do the checkout/pull in the AOMP repository. The file "bin/aomp_common_vars" lists the branches of each repository for a particular AOMP release. In the master branch of AOMP, aomp_common_vars lists the development branches. It is a good idea to run clone_aomp.sh twice after you checkout a release to be sure you pulled all the checkouts for a particular release.

If your are interested in joining the development of AOMP, please read the details on the source build at [README](bin/README.md).
