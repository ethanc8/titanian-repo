# Release Notes for OpenCV 4.8.1-1+jnano

This was built from OpenCV 4.8.1.

It is optimized for NVIDIA CUDA and the NVIDIA GPU found on the NVIDIA Jetson Nano.

CPython 2 and 3 bindings are available, but not Java or JNI.

## CMake flags

```bash
cmake -D CMAKE_BUILD_TYPE=RELEASE \
-D CMAKE_INSTALL_PREFIX=/usr \
-D OPENCV_EXTRA_MODULES_PATH=$(realpath ../opencv_contrib/modules) \
-D EIGEN_INCLUDE_PATH=/usr/include/eigen3 \
-D WITH_OPENCL=OFF \
-D WITH_CUDA=ON \
-D CUDA_ARCH_BIN=5.3 \
-D CUDA_ARCH_PTX="" \
-D WITH_CUDNN=ON \
-D WITH_CUBLAS=ON \
-D ENABLE_FAST_MATH=ON \
-D CUDA_FAST_MATH=ON \
-D OPENCV_DNN_CUDA=ON \
-D ENABLE_NEON=ON \
-D WITH_QT=OFF \
-D WITH_OPENMP=ON \
-D BUILD_TIFF=ON \
-D WITH_FFMPEG=ON \
-D WITH_GSTREAMER=ON \
-D WITH_TBB=ON \
-D BUILD_TBB=ON \
-D BUILD_TESTS=OFF \
-D WITH_EIGEN=ON \
-D WITH_V4L=ON \
-D WITH_LIBV4L=ON \
-D WITH_PROTOBUF=ON \
-D OPENCV_ENABLE_NONFREE=ON \
-D INSTALL_C_EXAMPLES=OFF \
-D INSTALL_PYTHON_EXAMPLES=OFF \
-D PYTHON3_PACKAGES_PATH=/usr/lib/python3/dist-packages \
-D OPENCV_GENERATE_PKGCONFIG=ON \
-D BUILD_EXAMPLES=OFF ../opencv
```

## Checkinstall flags

```bash
fakeroot checkinstall --pkgname libopencv-titanian --pkgversion 4.8.1-1+jnano --arch arm64 --pkglicense Apache-2.0 --pkgsource opencv --maintainer "Ethan Charoenpitaks <echaroenpitaks@imsa.edu>" --provides "libopencv, libopencv-4.0.0, libopencv-dev, opencv-data, python3-opencv, python3-opencv-apps, python-opencv, python-opencv-apps, libopencv-apps-dev, libopencv-apps2d, libopencv-calib3d-dev, libopencv-calib3d406, libopencv-contrib-dev, libopencv-contrib406, libopencv-core-dev, libopencv-core406, libopencv-dnn-dev, libopencv-dnn406, libopencv-features2d-dev, libopencv-features2d406, libopencv-flann-dev, libopencv-flann406, libopencv-highgui-dev, libopencv-highgui406, libopencv-imgcodecs-dev, libopencv-imgcodecs406, libopencv-ml-dev, libopencv-ml406, libopencv-objdetect-dev, libopencv-objdetect406, libopencv-photo406, libopencv-shape-dev, libopencv-shape406, libopencv-stitching-dev, libopencv-stitching406, libopencv-superres-dev, libopencv-superres406, libopencv-video-dev, libopencv-video406, libopencv-videoio-dev, libopencv-videoio406, libopencv-videostab-dev, libopencv-videostab406, libopencv-viz-dev, libopencv-viz406" --requires "build-essential, cmake, git, unzip, pkg-config, zlib1g-dev, libjpeg-dev, libjpeg8-dev, libjpeg-turbo8-dev, libpng-dev, libtiff-dev, libavcodec-dev, libavformat-dev, libswscale-dev, libglew-dev, libgtk2.0-dev, libgtk-3-dev, libcanberra-gtk3-dev, python3-dev, python3-numpy, python3-pip, libxvidcore-dev, libx264-dev, libgtk-3-dev, libtbb2, libtbb-dev, libdc1394-22-dev, libxine2-dev, gstreamer1.0-tools, libv4l-dev, v4l-utils, qv4l2, libgstreamer-plugins-base1.0-dev, libgstreamer-plugins-good1.0-dev, libavresample-dev, libvorbis-dev, libxine2-dev, libtesseract-dev, libfaac-dev, libmp3lame-dev, libtheora-dev, libpostproc-dev, libopencore-amrnb-dev, libopencore-amrwb-dev, libopenblas-dev, libatlas-base-dev, libblas-dev, liblapack-dev, liblapacke-dev, libeigen3-dev, gfortran, libhdf5-dev, protobuf-compiler, libprotobuf-dev, libgoogle-glog-dev, libgflags-dev" --install=no --fstrans=yes
```

`/usr/lib/aarch64-linux-gnu/libtbb.so` was manually removed from the package.

## CMake output

```
-- General configuration for OpenCV 4.8.1 =====================================
--   Version control:               unknown
-- 
--   Extra modules:
--     Location (extra):            /home/titan/Projects/Projects/OpenCV/opencv_contrib/modules
--     Version control (extra):     unknown
-- 
--   Platform:
--     Timestamp:                   2024-01-03T04:51:36Z
--     Host:                        Linux 4.9.253-tegra aarch64
--     CMake:                       3.25.1
--     CMake generator:             Unix Makefiles
--     CMake build tool:            /usr/bin/make
--     Configuration:               RELEASE
-- 
--   CPU/HW features:
--     Baseline:                    NEON FP16
--       required:                  NEON
-- 
--   C/C++:
--     Built as dynamic libs?:      YES
--     C++ standard:                11
--     C++ Compiler:                /usr/bin/c++  (ver 7.5.0)
--     C++ flags (Release):         -fsigned-char -ffast-math -W -Wall -Wreturn-type -Wnon-virtual-dtor -Waddress -Wsequence-point -Wformat -Wformat-security -Wmissing-declarations -Wundef -Winit-self -Wpointer-arith -Wshadow -Wsign-promo -Wuninitialized -Wsuggest-override -Wno-delete-non-virtual-dtor -Wno-comment -Wimplicit-fallthrough=3 -Wno-strict-overflow -fdiagnostics-show-option -pthread -fomit-frame-pointer -ffunction-sections -fdata-sections    -fvisibility=hidden -fvisibility-inlines-hidden -fopenmp -O3 -DNDEBUG  -DNDEBUG
--     C++ flags (Debug):           -fsigned-char -ffast-math -W -Wall -Wreturn-type -Wnon-virtual-dtor -Waddress -Wsequence-point -Wformat -Wformat-security -Wmissing-declarations -Wundef -Winit-self -Wpointer-arith -Wshadow -Wsign-promo -Wuninitialized -Wsuggest-override -Wno-delete-non-virtual-dtor -Wno-comment -Wimplicit-fallthrough=3 -Wno-strict-overflow -fdiagnostics-show-option -pthread -fomit-frame-pointer -ffunction-sections -fdata-sections    -fvisibility=hidden -fvisibility-inlines-hidden -fopenmp -g  -O0 -DDEBUG -D_DEBUG
--     C Compiler:                  /usr/bin/cc
--     C flags (Release):           -fsigned-char -ffast-math -W -Wall -Wreturn-type -Waddress -Wsequence-point -Wformat -Wformat-security -Wmissing-declarations -Wmissing-prototypes -Wstrict-prototypes -Wundef -Winit-self -Wpointer-arith -Wshadow -Wuninitialized -Wno-comment -Wimplicit-fallthrough=3 -Wno-strict-overflow -fdiagnostics-show-option -pthread -fomit-frame-pointer -ffunction-sections -fdata-sections    -fvisibility=hidden -fopenmp -O3 -DNDEBUG  -DNDEBUG
--     C flags (Debug):             -fsigned-char -ffast-math -W -Wall -Wreturn-type -Waddress -Wsequence-point -Wformat -Wformat-security -Wmissing-declarations -Wmissing-prototypes -Wstrict-prototypes -Wundef -Winit-self -Wpointer-arith -Wshadow -Wuninitialized -Wno-comment -Wimplicit-fallthrough=3 -Wno-strict-overflow -fdiagnostics-show-option -pthread -fomit-frame-pointer -ffunction-sections -fdata-sections    -fvisibility=hidden -fopenmp -g  -O0 -DDEBUG -D_DEBUG
--     Linker flags (Release):      -Wl,--gc-sections -Wl,--as-needed -Wl,--no-undefined  
--     Linker flags (Debug):        -Wl,--gc-sections -Wl,--as-needed -Wl,--no-undefined  
--     ccache:                      NO
--     Precompiled headers:         NO
--     Extra dependencies:          m pthread cudart_static dl rt nppc nppial nppicc nppicom nppidei nppif nppig nppim nppist nppisu nppitc npps cublas cudnn cufft -L/usr/local/cuda/lib64 -L/usr/lib/aarch64-linux-gnu
--     3rdparty dependencies:
-- 
--   OpenCV modules:
--     To be built:                 alphamat aruco bgsegm bioinspired calib3d ccalib core cudaarithm cudabgsegm cudacodec cudafeatures2d cudafilters cudaimgproc cudalegacy cudaobjdetect cudaoptflow cudastereo cudawarping cudev datasets dnn dnn_objdetect dnn_superres dpm face features2d flann freetype fuzzy gapi hdf hfs highgui img_hash imgcodecs imgproc intensity_transform line_descriptor mcc ml objdetect optflow phase_unwrapping photo plot python2 python3 quality rapid reg rgbd saliency sfm shape stereo stitching structured_light superres surface_matching text tracking ts video videoio videostab wechat_qrcode xfeatures2d ximgproc xobjdetect xphoto
--     Disabled:                    world
--     Disabled by dependency:      -
--     Unavailable:                 cvv java julia matlab ovis viz
--     Applications:                perf_tests apps
--     Documentation:               NO
--     Non-free algorithms:         YES
-- 
--   GUI:                           GTK3
--     GTK+:                        YES (ver 3.22.30)
--       GThread :                  YES (ver 2.56.4)
--       GtkGlExt:                  NO
--     VTK support:                 NO
-- 
--   Media I/O: 
--     ZLib:                        /usr/lib/aarch64-linux-gnu/libz.so (ver 1.2.11)
--     JPEG:                        /usr/lib/aarch64-linux-gnu/libjpeg.so (ver 80)
--     WEBP:                        build (ver encoder: 0x020f)
--     PNG:                         /usr/lib/aarch64-linux-gnu/libpng.so (ver 1.6.34)
--     TIFF:                        build (ver 42 - 4.2.0)
--     JPEG 2000:                   build (ver 2.5.0)
--     OpenEXR:                     build (ver 2.3.0)
--     HDR:                         YES
--     SUNRASTER:                   YES
--     PXM:                         YES
--     PFM:                         YES
-- 
--   Video I/O:
--     DC1394:                      YES (2.2.5)
--     FFMPEG:                      YES
--       avcodec:                   YES (57.107.100)
--       avformat:                  YES (57.83.100)
--       avutil:                    YES (55.78.100)
--       swscale:                   YES (4.8.100)
--       avresample:                YES (3.7.0)
--     GStreamer:                   YES (1.14.5)
--     v4l/v4l2:                    YES (linux/videodev2.h)
-- 
--   Parallel framework:            TBB (ver 2020.2 interface 11102)
-- 
--   Trace:                         YES (with Intel ITT)
-- 
--   Other third-party libraries:
--     Lapack:                      YES (/usr/lib/aarch64-linux-gnu/liblapack.so /usr/lib/aarch64-linux-gnu/libcblas.so /usr/lib/aarch64-linux-gnu/libatlas.so)
--     Eigen:                       YES (ver 3.3.4)
--     Custom HAL:                  YES (carotene (ver 0.0.1))
--     Protobuf:                    build (3.19.1)
--     Flatbuffers:                 builtin/3rdparty (23.5.9)
-- 
--   NVIDIA CUDA:                   YES (ver 10.2, CUFFT CUBLAS FAST_MATH)
--     NVIDIA GPU arch:             53
--     NVIDIA PTX archs:
-- 
--   cuDNN:                         YES (ver 8.2.1)
-- 
--   Python 2:
--     Interpreter:                 /usr/bin/python2.7 (ver 2.7.17)
--     Libraries:                   /usr/lib/aarch64-linux-gnu/libpython2.7.so (ver 2.7.17)
--     numpy:                       /usr/lib/python2.7/dist-packages/numpy/core/include (ver 1.13.3)
--     install path:                lib/python2.7/dist-packages/cv2/python-2.7
-- 
--   Python 3:
--     Interpreter:                 /usr/bin/python3 (ver 3.6.9)
--     Libraries:                   /usr/lib/aarch64-linux-gnu/libpython3.6m.so (ver 3.6.9)
--     numpy:                       /usr/lib/python3/dist-packages/numpy/core/include (ver 1.13.3)
--     install path:                /usr/lib/python3/dist-packages/cv2/python-3.6
-- 
--   Python (for build):            /usr/bin/python2.7
-- 
--   Java:                          
--     ant:                         NO
--     Java:                        NO
--     JNI:                         NO
--     Java wrappers:               NO
--     Java tests:                  NO
-- 
--   Install to:                    /usr
-- -----------------------------------------------------------------
```