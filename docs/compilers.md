---
title: Supported Compilers
---

Though it's 2017 already, the support for C++11 is still a bit sparse. Currently, the following compilers are known to work:

- GCC 4.9 - 7.2 (and possibly later)
- Clang 3.4 - 5.0 (and possibly later)
- Intel C++ Compiler 17.0.2 (and possibly later)
- Microsoft Visual C++ 2015 / Build Tools 14.0.25123.0 (and possibly later)
- Microsoft Visual C++ 2017 / Build Tools 15.5.180.51428 (and possibly later)

I would be happy to learn about other compilers/versions.

## Notes

- GCC 4.8 does not work because of two bugs ([55817](https://gcc.gnu.org/bugzilla/show_bug.cgi?id=55817) and [57824](https://gcc.gnu.org/bugzilla/show_bug.cgi?id=57824)) in the C++11 support. Note there is a [pull request](https://github.com/nlohmann/json/pull/212) to fix some of the issues.
- Android defaults to using very old compilers and C++ libraries. To fix this, add the following to your `Application.mk`. This will switch to the LLVM C++ library, the Clang compiler, and enable C++11 and other features disabled by default.
 
    ```
    APP_STL := c++_shared
    NDK_TOOLCHAIN_VERSION := clang3.6
    APP_CPPFLAGS += -frtti -fexceptions
    ```
 
    The code compiles successfully with [Android NDK](https://developer.android.com/ndk/index.html?hl=ml), Revision 9 - 11 (and possibly later) and [CrystaX's Android NDK](https://www.crystax.net/en/android/ndk) version 10.

- For GCC running on MinGW or Android SDK, the error `'to_string' is not a member of 'std'` (or similarly, for `strtod`) may occur. Note this is not an issue with the code,  but rather with the compiler itself. On Android, see above to build with a newer environment.  For MinGW, please refer to [this site](http://tehsausage.com/mingw-to-string) and [this discussion](https://github.com/nlohmann/json/issues/136) for information on how to fix this bug. For Android NDK using `APP_STL := gnustl_static`, please refer to [this discussion](https://github.com/nlohmann/json/issues/219).

## Continuous Integration

The following compilers are currently used in continuous integration at [Travis](https://travis-ci.org/nlohmann/json) and [AppVeyor](https://ci.appveyor.com/project/nlohmann/json):

| Compiler        | Operating System             | Version String |
|-----------------|------------------------------|----------------|
| GCC 4.9.4       | Ubuntu 14.04.5 LTS           | g++-4.9 (Ubuntu 4.9.4-2ubuntu1~14.04.1) 4.9.4 |
| GCC 5.4.1       | Ubuntu 14.04.5 LTS           | g++-5 (Ubuntu 5.4.1-2ubuntu1~14.04) 5.4.1 20160904 |
| GCC 6.3.0       | Ubuntu 14.04.5 LTS           | g++-6 (Ubuntu/Linaro 6.3.0-18ubuntu2~14.04) 6.3.0 20170519 |
| GCC 7.1.0       | Ubuntu 14.04.5 LTS           | g++-7 (Ubuntu 7.1.0-5ubuntu2~14.04) 7.1.0
| Clang 3.5.0     | Ubuntu 14.04.5 LTS           | clang version 3.5.0-4ubuntu2~trusty2 (tags/RELEASE_350/final) |
| Clang 3.6.2     | Ubuntu 14.04.5 LTS           | clang version 3.6.2-svn240577-1~exp1 (branches/release_36) |
| Clang 3.7.1     | Ubuntu 14.04.5 LTS           | clang version 3.7.1-svn253571-1~exp1 (branches/release_37) |
| Clang 3.8.0     | Ubuntu 14.04.5 LTS           | clang version 3.8.0-2ubuntu3~trusty5 (tags/RELEASE_380/final) |
| Clang 3.9.1     | Ubuntu 14.04.5 LTS           | clang version 3.9.1-4ubuntu3~14.04.2 (tags/RELEASE_391/rc2) |
| Clang 4.0.1     | Ubuntu 14.04.5 LTS           | clang version 4.0.1-svn305264-1~exp1 (branches/release_40) |
| Clang 5.0.0     | Ubuntu 14.04.5 LTS           | clang version 5.0.0-svn310902-1~exp1 (branches/release_50) |
| Clang Xcode 6.4 | Darwin Kernel Version 14.3.0 (OSX 10.10.3) | Apple LLVM version 6.1.0 (clang-602.0.53) (based on LLVM 3.6.0svn) |
| Clang Xcode 7.3 | Darwin Kernel Version 15.0.0 (OSX 10.10.5) | Apple LLVM version 7.3.0 (clang-703.0.29) |
| Clang Xcode 8.0 | Darwin Kernel Version 15.6.0 | Apple LLVM version 8.0.0 (clang-800.0.38) |
| Clang Xcode 8.1 | Darwin Kernel Version 16.1.0 (macOS 10.12.1) | Apple LLVM version 8.0.0 (clang-800.0.42.1) |
| Clang Xcode 8.2 | Darwin Kernel Version 16.1.0 (macOS 10.12.1) | Apple LLVM version 8.0.0 (clang-800.0.42.1) |
| Clang Xcode 8.3 | Darwin Kernel Version 16.5.0 (macOS 10.12.4) | Apple LLVM version 8.1.0 (clang-802.0.38) |
| Clang Xcode 9.0 | Darwin Kernel Version 16.7.0 (macOS 10.12.6) | Apple LLVM version 9.0.0 (clang-900.0.37) |
| Clang Xcode 9.1 | Darwin Kernel Version 16.7.0 (macOS 10.12.6) | Apple LLVM version 9.0.0 (clang-900.0.38) |
| Clang Xcode 9.2 | Darwin Kernel Version 16.7.0 (macOS 10.12.6) | Apple LLVM version 8.1.0 (clang-900.0.39.2) |
| Visual Studio 14 2015 | Windows Server 2012 R2 (x64) | Microsoft (R) Build Engine version 14.0.25420.1, MSVC 19.0.24215.1 | 
| Visual Studio 2017 | Windows Server 2016 | Microsoft (R) Build Engine version 15.5.180.51428, MSVC 19.12.25830.2 |
