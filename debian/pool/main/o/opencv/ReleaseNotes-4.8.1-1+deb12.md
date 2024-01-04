# Release Notes for OpenCV 4.8.1-1+deb12

This was built from OpenCV 4.8.1.

It is optimized for NVIDIA CUDA, and to use the CUDA features requires a NVIDIA GPU with compute capability of 5.0 or higher (Maxwell or newer microarchitecture). Please see [NVIDIA's website](https://developer.nvidia.com/cuda-gpus) to determine if your GPU is compatible.

If you do not have a CUDA-compatible GPU, this OpenCV also supports running entirely on the CPU or on your GPU via OpenCL.

CPython 3 bindings are available, but not Java, JNI, or CPython 2.

## CMake flags

```bash
export CUDA_BIN_PATH=/usr
cmake -D CMAKE_BUILD_TYPE=RELEASE \
-D CMAKE_INSTALL_PREFIX=/usr \
-D OPENCV_EXTRA_MODULES_PATH=$(realpath ../opencv_contrib/modules) \
-D EIGEN_INCLUDE_PATH=/usr/include/eigen3 \
-D WITH_OPENCL=ON \
-D WITH_CUDA=ON \
-D CUDA_BIN_PATH=/usr \
-D CUDA_TOOLKIT_ROOT_DIR=/usr \
-D CUDA_HOST_COMPILER=/usr/bin/cuda-gcc \
-D CUDA_ARCH_BIN="8.9 8.6 7.5 7.0 6.1 5.2 5.0" \
-D CUDA_ARCH_PTX="8.9 8.6 7.5 7.0 6.1 5.2 5.0" \
-D WITH_CUDNN=ON \
-D WITH_CUBLAS=ON \
-D ENABLE_FAST_MATH=ON \
-D CUDA_FAST_MATH=ON \
-D OPENCV_DNN_CUDA=ON \
-D CUDNN_LIBRARY="/usr/lib/x86_64-linux-gnu/libcudnn.so.8.5.0" \
-D CUDNN_INCLUDE_DIR="/usr/include/x86_64-linux-gnu/" \
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
fakeroot checkinstall --pkgname libopencv-titanian --pkgversion 4.8.1-1+deb12 --arch amd64 --pkglicense Apache-2.0 --pkgsource opencv --maintainer "Ethan Charoenpitaks <echaroenpitaks@imsa.edu>" --provides "libopencv, libopencv-dev, opencv-data, python3-opencv, python3-opencv-apps, libopencv-apps-dev, libopencv-apps2d, libopencv-calib3d-dev, libopencv-calib3d406, libopencv-contrib-dev, libopencv-contrib406, libopencv-core-dev, libopencv-core406, libopencv-dnn-dev, libopencv-dnn406, libopencv-features2d-dev, libopencv-features2d406, libopencv-flann-dev, libopencv-flann406, libopencv-highgui-dev, libopencv-highgui406, libopencv-imgcodecs-dev, libopencv-imgcodecs406, libopencv-ml-dev, libopencv-ml406, libopencv-objdetect-dev, libopencv-objdetect406, libopencv-photo406, libopencv-shape-dev, libopencv-shape406, libopencv-stitching-dev, libopencv-stitching406, libopencv-superres-dev, libopencv-superres406, libopencv-video-dev, libopencv-video406, libopencv-videoio-dev, libopencv-videoio406, libopencv-videostab-dev, libopencv-videostab406, libopencv-viz-dev, libopencv-viz406" --requires "build-essential, cmake, git, unzip, pkg-config, zlib1g-dev, libjpeg-dev, libjpeg62-turbo-dev, libpng-dev, libtiff-dev, libavcodec-dev, libavformat-dev, libswscale-dev, libglew-dev, libgtk2.0-dev, libgtk-3-dev, libcanberra-gtk3-dev, python3-dev, python3-numpy, python3-pip, libxvidcore-dev, libx264-dev, libgtk-3-dev, libtbb-dev, libdc1394-dev, libxine2-dev, gstreamer1.0-tools, libv4l-dev, v4l-utils, qv4l2, gstreamer1.0-plugins-good, gstreamer1.0-plugins-base, libgstreamer-plugins-base1.0-dev, libswresample-dev, libvorbis-dev, libxine2-dev, libtesseract-dev, libmp3lame-dev, libtheora-dev, libpostproc-dev, libopencore-amrnb-dev, libopencore-amrwb-dev, libopenblas-dev, libatlas-base-dev, libblas-dev, liblapack-dev, liblapacke-dev, libeigen3-dev, gfortran, libhdf5-dev, protobuf-compiler, libprotobuf-dev, libgoogle-glog-dev, libgflags-dev, python3-numpy, nvidia-cuda-dev, nvidia-cuda-toolkit, nvidia-cudnn" --install=no --fstrans=yes
```

`/usr/lib/libtbb.so` was manually removed from the package.

## CMake output

```
-- General configuration for OpenCV 4.8.1 =====================================
--   Version control:               4.8.1
-- 
--   Extra modules:
--     Location (extra):            /home/titan/Projects/OpenCV/opencv_contrib/modules
--     Version control (extra):     4.8.1
-- 
--   Platform:
--     Timestamp:                   2024-01-03T16:55:31Z
--     Host:                        Linux 6.1.0-17-amd64 x86_64
--     CMake:                       3.25.1
--     CMake generator:             Unix Makefiles
--     CMake build tool:            /usr/bin/gmake
--     Configuration:               RELEASE
-- 
--   CPU/HW features:
--     Baseline:                    SSE SSE2 SSE3
--       requested:                 SSE3
--     Dispatched code generation:  SSE4_1 SSE4_2 FP16 AVX AVX2 AVX512_SKX
--       requested:                 SSE4_1 SSE4_2 AVX FP16 AVX2 AVX512_SKX
--       SSE4_1 (16 files):         + SSSE3 SSE4_1
--       SSE4_2 (1 files):          + SSSE3 SSE4_1 POPCNT SSE4_2
--       FP16 (0 files):            + SSSE3 SSE4_1 POPCNT SSE4_2 FP16 AVX
--       AVX (7 files):             + SSSE3 SSE4_1 POPCNT SSE4_2 AVX
--       AVX2 (35 files):           + SSSE3 SSE4_1 POPCNT SSE4_2 FP16 FMA3 AVX AVX2
--       AVX512_SKX (5 files):      + SSSE3 SSE4_1 POPCNT SSE4_2 FP16 FMA3 AVX AVX2 AVX_512F AVX512_COMMON AVX512_SKX
-- 
--   C/C++:
--     Built as dynamic libs?:      YES
--     C++ standard:                11
--     C++ Compiler:                /usr/bin/c++  (ver 12.2.0)
--     C++ flags (Release):         -fsigned-char -ffast-math -W -Wall -Wreturn-type -Wnon-virtual-dtor -Waddress -Wsequence-point -Wformat -Wformat-security -Wmissing-declarations -Wundef -Winit-self -Wpointer-arith -Wshadow -Wsign-promo -Wuninitialized -Wsuggest-override -Wno-delete-non-virtual-dtor -Wno-comment -Wimplicit-fallthrough=3 -Wno-strict-overflow -fdiagnostics-show-option -Wno-long-long -pthread -fomit-frame-pointer -ffunction-sections -fdata-sections  -msse -msse2 -msse3 -fvisibility=hidden -fvisibility-inlines-hidden -fopenmp -O3 -DNDEBUG  -DNDEBUG
--     C++ flags (Debug):           -fsigned-char -ffast-math -W -Wall -Wreturn-type -Wnon-virtual-dtor -Waddress -Wsequence-point -Wformat -Wformat-security -Wmissing-declarations -Wundef -Winit-self -Wpointer-arith -Wshadow -Wsign-promo -Wuninitialized -Wsuggest-override -Wno-delete-non-virtual-dtor -Wno-comment -Wimplicit-fallthrough=3 -Wno-strict-overflow -fdiagnostics-show-option -Wno-long-long -pthread -fomit-frame-pointer -ffunction-sections -fdata-sections  -msse -msse2 -msse3 -fvisibility=hidden -fvisibility-inlines-hidden -fopenmp -g  -O0 -DDEBUG -D_DEBUG
--     C Compiler:                  /usr/bin/cc
--     C flags (Release):           -fsigned-char -ffast-math -W -Wall -Wreturn-type -Waddress -Wsequence-point -Wformat -Wformat-security -Wmissing-declarations -Wmissing-prototypes -Wstrict-prototypes -Wundef -Winit-self -Wpointer-arith -Wshadow -Wuninitialized -Wno-comment -Wimplicit-fallthrough=3 -Wno-strict-overflow -fdiagnostics-show-option -Wno-long-long -pthread -fomit-frame-pointer -ffunction-sections -fdata-sections  -msse -msse2 -msse3 -fvisibility=hidden -fopenmp -O3 -DNDEBUG  -DNDEBUG
--     C flags (Debug):             -fsigned-char -ffast-math -W -Wall -Wreturn-type -Waddress -Wsequence-point -Wformat -Wformat-security -Wmissing-declarations -Wmissing-prototypes -Wstrict-prototypes -Wundef -Winit-self -Wpointer-arith -Wshadow -Wuninitialized -Wno-comment -Wimplicit-fallthrough=3 -Wno-strict-overflow -fdiagnostics-show-option -Wno-long-long -pthread -fomit-frame-pointer -ffunction-sections -fdata-sections  -msse -msse2 -msse3 -fvisibility=hidden -fopenmp -g  -O0 -DDEBUG -D_DEBUG
--     Linker flags (Release):      -Wl,--exclude-libs,libippicv.a -Wl,--exclude-libs,libippiw.a   -Wl,--gc-sections -Wl,--as-needed -Wl,--no-undefined  
--     Linker flags (Debug):        -Wl,--exclude-libs,libippicv.a -Wl,--exclude-libs,libippiw.a   -Wl,--gc-sections -Wl,--as-needed -Wl,--no-undefined  
--     ccache:                      NO
--     Precompiled headers:         NO
--     Extra dependencies:          m pthread cudart_static dl rt nppc nppial nppicc nppidei nppif nppig nppim nppist nppisu nppitc npps cublas cudnn cufft -L/usr/lib/x86_64-linux-gnu
--     3rdparty dependencies:
-- 
--   OpenCV modules:
--     To be built:                 alphamat aruco bgsegm bioinspired calib3d ccalib core cudaarithm cudabgsegm cudacodec cudafeatures2d cudafilters cudaimgproc cudalegacy cudaobjdetect cudaoptflow cudastereo cudawarping cudev datasets dnn dnn_objdetect dnn_superres dpm face features2d flann freetype fuzzy gapi hdf hfs highgui img_hash imgcodecs imgproc intensity_transform line_descriptor mcc ml objdetect optflow phase_unwrapping photo plot python3 quality rapid reg rgbd saliency sfm shape stereo stitching structured_light superres surface_matching text tracking ts video videoio videostab wechat_qrcode xfeatures2d ximgproc xobjdetect xphoto
--     Disabled:                    world
--     Disabled by dependency:      -
--     Unavailable:                 cvv java julia matlab ovis python2 viz
--     Applications:                perf_tests apps
--     Documentation:               NO
--     Non-free algorithms:         YES
-- 
--   GUI:                           GTK3
--     GTK+:                        YES (ver 3.24.38)
--       GThread :                  YES (ver 2.74.6)
--       GtkGlExt:                  NO
--     VTK support:                 NO
-- 
--   Media I/O: 
--     ZLib:                        /usr/lib/x86_64-linux-gnu/libz.so (ver 1.2.13)
--     JPEG:                        /usr/lib/x86_64-linux-gnu/libjpeg.so (ver 62)
--     WEBP:                        /usr/lib/x86_64-linux-gnu/libwebp.so (ver encoder: 0x020f)
--     PNG:                         /usr/lib/x86_64-linux-gnu/libpng.so (ver 1.6.39)
--     TIFF:                        build (ver 42 - 4.2.0)
--     JPEG 2000:                   build (ver 2.5.0)
--     OpenEXR:                     build (ver 2.3.0)
--     HDR:                         YES
--     SUNRASTER:                   YES
--     PXM:                         YES
--     PFM:                         YES
-- 
--   Video I/O:
--     DC1394:                      YES (2.2.6)
--     FFMPEG:                      YES
--       avcodec:                   YES (59.37.100)
--       avformat:                  YES (59.27.100)
--       avutil:                    YES (57.28.100)
--       swscale:                   YES (6.7.100)
--       avresample:                NO
--     GStreamer:                   YES (1.22.0)
--     v4l/v4l2:                    YES (linux/videodev2.h)
-- 
--   Parallel framework:            TBB (ver 2020.2 interface 11102)
-- 
--   Trace:                         YES (with Intel ITT)
-- 
--   Other third-party libraries:
--     Intel IPP:                   2021.8 [2021.8.0]
--            at:                   /home/titan/Projects/OpenCV/build2/3rdparty/ippicv/ippicv_lnx/icv
--     Intel IPP IW:                sources (2021.8.0)
--               at:                /home/titan/Projects/OpenCV/build2/3rdparty/ippicv/ippicv_lnx/iw
--     VA:                          NO
--     Lapack:                      YES (/usr/lib/x86_64-linux-gnu/liblapack.so /usr/lib/x86_64-linux-gnu/libcblas.so /usr/lib/x86_64-linux-gnu/libatlas.so)
--     Eigen:                       YES (ver 3.4.0)
--     Custom HAL:                  NO
--     Protobuf:                    build (3.19.1)
--     Flatbuffers:                 builtin/3rdparty (23.5.9)
-- 
--   NVIDIA CUDA:                   YES (ver 11.8, CUFFT CUBLAS FAST_MATH)
--     NVIDIA GPU arch:             89 86 75 70 61 52 50
--     NVIDIA PTX archs:            89 86 75 70 61 52 50
-- 
--   cuDNN:                         YES (ver 8.5.0)
-- 
--   OpenCL:                        YES (no extra features)
--     Include path:                /home/titan/Projects/OpenCV/opencv/3rdparty/include/opencl/1.2
--     Link libraries:              Dynamic load
-- 
--   Python 3:
--     Interpreter:                 /usr/bin/python3 (ver 3.11.2)
--     Libraries:                   /usr/lib/x86_64-linux-gnu/libpython3.11.so (ver 3.11.2)
--     numpy:                       /usr/lib/python3/dist-packages/numpy/core/include (ver 1.24.2)
--     install path:                /usr/lib/python3/dist-packages/cv2/python-3.11
-- 
--   Python (for build):            /usr/bin/python3
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