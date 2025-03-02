Build of WPIMath from [wpilibsuite/allwpilib](https://github.com/wpilibsuite/allwpilib) at `v2025.3.1`. Built on Debian trixie amd64.

## Building

Protobuf packages (not sure if used): `libprotobuf-dev`, `libprotoc-dev`, `protobuf-compiler`

```bash

cmake -G "Unix Makefiles" \
               -D BUILD_SHARED_LIBS=ON \
               -D WITH_CSCORE=OFF \
               -D WITH_EXAMPLES=OFF \
               -D WITH_GUI=OFF \
               -D WITH_JAVA=OFF \
               -D WITH_NTCORE=ON \
               -D WITH_SIMULATION_MODULES=OFF \
               -D WITH_TESTS=OFF \
               -D WITH_WPILIB=OFF \
               -D WITH_WPIMATH=ON \
               -D WITH_PROTOBUF=OFF \
               -DProtobuf_PROTOC_EXECUTABLE=/usr/bin/protoc \
               ..
```

## Installation

```bash
fakeroot checkinstall --pkgname wpimath-titanian --pkgversion 2025.3.1+deb13 --arch amd64 --pkglicense Apache-2.0 --pkgsource allwpilib --maintainer "Ethan Charoenpitaks <echaroenpitaks@imsa.edu>" --install=no --fstrans=yes
 ```