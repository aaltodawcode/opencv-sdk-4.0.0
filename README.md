# OpenCV with support for OpenCL

This module is a precompiled sdk for **arm64-v4a** devices that has extended support for OpenCL in Android. 


### How to install
First clone the repository as a submodule:
```sh
$ git submodule add https://github.com/aaltodawcode/opencv-sdk-4.0.0.git
```
From *Android Studio* go to *`File`* &rarr; `New` &rarr; `Import Module...` and select **opencv-sdk-4.0.0**. 

Good job! Now your project has inherited OpenCV repository. However there is still one step to do.

From  the *Project* view of Android Studio, right click on your project and go to `Open Module Settings`, click on Tab `Dependencies` and add a new one with the button `+` and select **Implementation** as scope. 


### Compatibility with NDK
This library can be used also for NDK development in **C++**. To enable this feature, add the following lines to your *CmakeLists.txt* file:

```sh
set(CMAKE_BUILD_TYPE Release) # Tell the compiler to optimize compilation
set(ANDROID_NDK_ABI arm64-v8a) # Set only valid ABI
set( lib_src_DIR ${CMAKE_CURRENT_SOURCE_DIR}/../opencv-sdk-4.0.0 )

add_library(lib_opencv SHARED IMPORTED)

set_target_properties(lib_opencv PROPERTIES IMPORTED_LOCATION ${lib_src_DIR}/native/libs/arm64-v8a/libopencv_java4.so)

include_directories(${lib_src_DIR}/native/jni/include)
```

---
**NOTE**

If the program fails with error "library opencv-sdk-4.0.0 already imported" add the following line to *settings.gradle*:
```
include ':opencv-sdk-4.0.0'
```
---

### Contributor ###
- [Jacopo Bufalino](https://github.com/jackap)
