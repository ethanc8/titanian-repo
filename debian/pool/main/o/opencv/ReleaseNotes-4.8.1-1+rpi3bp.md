# OpenCV build 4.8.1-1+titan2022+rpi3bp

This build was built from OpenCV 4.8.1 (upstream) on a Raspberry Pi 3B+ running Raspberry Pi OS 12 Bookworm (64-bit).

It does not use OpenCL or CUDA, as those are not available on Raspberry Pi 3B+.

## Installation Instructions

```bash
wget -OL # URL to DEB package
sudo apt install ./opencv_4.8.1-1+titan2022+rpi3bp-1_arm64.deb
```

## CMake flags

```bash
cmake -DCMAKE_BUILD_TYPE=RELEASE -DCMAKE_INSTALL_PREFIX=/usr/local -DWITH_TBB=ON -DWITH_LAPACK=ON -DBUILD_TESTS=OFF -DINSTALL_C_EXAMPLES=OFF -DINSTALL_PYTHON_EXAMPLES=OFF -DBUILD_EXAMPLES=OFF -DOPENCV_EXTRA_MODULES_PATH=~/Projects/OpenCV/opencv_contrib/modules ../opencv
```

* `-DWITH_TBB` enables multithreading
* `-DWITH_LAPACK` enables OpenBLAS-based fast matrix operations
* `-DBUILD_TESTS=OFF -DINSTALL_C_EXAMPLES=OFF -DINSTALL_PYTHON_EXAMPLES=OFF -DBUILD_EXAMPLES=OFF` disables building tests and examples, so build time is less

## Checkinstall flags

```bash
fakeroot checkinstall --pkgname libopencv-dev --pkgversion 4.8.1-1+titan2022+rpi3bp --arch arm64 --pkglicense Apache-2.0 --pkgsource opencv --maintainer "Ethan Charoenpitaks <echaroenpitaks@imsa.edu>" --provides opencv --requires "git, build-essential, cmake, pkg-config, checkinstall, libjpeg-dev, libpng-dev, libtiff-dev, libtiff5-dev, libpng-dev, libprotobuf-dev, protobuf-compiler, libv4l-dev, libavcodec-dev, libavformat-dev, libswscale-dev, libgtk2.0-dev, libeigen3-dev, libv4l-dev, libxvidcore-dev, libx264-dev, libgtk-3-dev, libatlas-base-dev, libtbb-dev, libopenblas-dev, liblapacke-dev, python3-dev, python3-numpy, libgstreamer-plugins-base1.0-dev, libgstreamer1.0-dev, libgflags-dev, libgoogle-glog-dev, libdc1394-dev, tesseract-ocr, libtesseract-dev" --install=no --fstrans=yes
sudo apt install ./opencv*.deb
```

## Included Components

```
--     To be built:                 alphamat aruco bgsegm bioinspired calib3d ccalib core datasets dnn dnn_objdetect dnn_superres dpm face features2d flann freetype fuzzy gapi hfs highgui img_hash imgcodecs imgproc intensity_transform line_descriptor mcc ml objdetect optflow phase_unwrapping photo plot python3 quality rapid reg rgbd saliency sfm shape stereo stitching structured_light superres surface_matching text tracking ts video videoio videostab wechat_qrcode xfeatures2d ximgproc xobjdetect xphoto
--     Disabled:                    world
--     Disabled by dependency:      -
--     Unavailable:                 cudaarithm cudabgsegm cudacodec cudafeatures2d cudafilters cudaimgproc cudalegacy cudaobjdetect cudaoptflow cudastereo cudawarping cudev cvv hdf java julia matlab ovis python2 viz
--     Applications:                perf_tests apps
```