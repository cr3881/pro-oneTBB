# oneTBB examples
This is a forked repo. the original repo uses makefile, which is a little hard for windows developer, and intel has a better installer on windows than on linux as my experience. Therefore, I make a CMakeLists.txt to make my learning experience better. The original repo master branch is too old. oneTBB branch is up to date.
# intel oneAPI installer
https://registrationcenter-download.intel.com/akdlm/IRC_NAS/ae29263e-38b9-4d43-86c3-376d6e0668e7/intel-oneapi-base-toolkit-2025.0.1.47_offline.exe
the full installation takes too much space. proTBB exaples depends on oneDPL, at least for chapter #1. And oneDPL is part of DPC++ library. Therefore, you have to install DPC++ component. I have not verify other components. 
oneDPL is a header only library. Therefore, it might be easier to clone from https://github.com/oneapi-src/oneDPL directly. I will try it on linux.
# intel library environment variables
Make sure to run "C:\\Program Files (x86)\\Intel\\oneAPI\\setvars.bat" before running cmake script. it sets up env variables for the cmake scripts, otherwise, cmake does not know how to load intel library. vs2022 works fine, and you can try intel compiler too. 


#ORIGINAL README.
# SourceCode

Source code of the examples provided in each chapter of the TBB book (2019).

**This branch is a WORK IN PROGRESS to update examples our 2019 book (TBB) for the forthcoming 2022 book (oneTBB)**

Makefiles default to use of Intel C++ compiler, but specifying a CXX definition
on the command line can change the compilation to be with Microsoft (CXX=cl),
XCode (CXX=clang++), or Gnu C++ (CXX=g++).

TBB, which is needed of course, can be installed as part of the
Intel compiler install, or obtained separately.

The following commands worked for us prior to the release of the book:
on MacOS and Linux: make
on MacOS and Linux: make CXX=g++
on Windows: nmake /f Makefile.nmake
on Windows: nmake /f Makefile.nmake CXX=cl
(the latter requires use of vcvars64.bat (Visual Studio),
 and setting of INCLUDE environment variable to include
 the windows\tbb\include and windows\pstl\include
 directories in your TBB installation, and setting of
 LIB environment variable to search the
 tbb\lib\ia32_win\vc_mt and tbb\lib\intel64_win\vc_mt
 directories.)

---

Linux or Mac builds with: make
(clean up with: make clean)

Windows build with: nmake /f Makefile.nmake
(clean up with: nmake /f Makefile.nmake clean)

---

Ch18 and Ch19 (Chapters 18-19) require an OpenCL SDK to be installed (vendor of choice).
Khronos maintains a list at https://www.khronos.org/conformance/adopters/conformant-products/opencl
Intel's SDK is at https://software.intel.com/intel-opencl
NVidia's SDK is at https://developer.nvidia.com/opencl

Ch20 (Chapter 20) require that the hwloc library to be installed.
https://www.open-mpi.org/projects/hwloc/

Feel free to leave comments/suggestions/feedback on the git project website for the book.

Mike, Rafa, and James
