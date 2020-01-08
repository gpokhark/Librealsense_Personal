# Proxy Setup
Proxy variables required to setup before the installation - 
```cmd
setx -m ALL_PROXY http://proxy-xyz.com:10
setx -m http_proxy http://proxy-xyz.com:10
setx -m https_proxy https://proxy-xyz.com:10
``` 

# Librealsense setup
This is step by step guide on how to setup intel [realsense library](git@github.com:IntelRealSense/librealsense.git) for the realsense depth camera.
1. `git clone git@github.com:IntelRealSense/librealsense.git` and or download and unzip the source code from [here](https://github.com/IntelRealSense/librealsense/releases).
2. `cd librealsense/`, lets call this directory `%LIBREALSENSE_DIR%`.
3. `mkdir build && cd build/`
4. For windows follow the steps given [here](https://github.com/IntelRealSense/librealsense/blob/master/doc/installation_windows.md#cmake_snapshot_win) and also do read this -> [Intel Realsense Installation Guide](https://visp-doc.inria.fr/doxygen/visp-3.2.0/tutorial-install-win10-msvc15.html).
5. `cmake -G "Visual Studio 14 2015" -A "x64" "C:\xyz\Intel_Realsense\librealsense-2.30.0" -DCMAKE_INSTALL_PREFIX="C:\xyz\Intel_Realsense\librealsense-2.30.0\build"`
6. `cmake --build . --config Release --target install` run as administrator.
7. `cmake --build . --config Debug --target install` run as administrator.
8. Create `REALSENSE2_DIR` variable in the environment - `setx -m REALSENSE2_DIR "C:\xyz\Intel_Realsense\librealsense-2.30.0\build\lib\cmake"` 
9. Add to the `Path` variable - `%REALSENSE2_DIR%\..\..\bin`.

# Compile and Run a project
To compile and run the project set up the `Path` variables for the `librealsense2` and `OpenCV` libraries. 
Install the latest version of [cmake](https://cmake.org/download/).

Then follow the steps - 
```cmd
cd $PROJECTDIR
mkdir build
cd build
cmake ..
cmake --build .
```