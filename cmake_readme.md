# CMake conversion

CMake conversion tips from
 http://stackoverflow.com/questions/7132862/tutorial-for-converting-autotools-to-cmake

Helpful comparison from 
 https://github.com/google/snappy/pull/16/files

CMake manual at
 https://cmake.org/cmake/help/v2.8.8/cmake.html

## History

Build autotools version with

    ./autogen.sh #(`autoreconf -fi`)
    ./configure --without-libidn > cmake_configure_autotools.log
    make --trace > cmake_make_autotools.log

Build cmake version with

    cmake -E make_directory build
    cd build
    cmake ..
    make VERBOSE=1
