# CMake conversion

CMake conversion tips from
 http://stackoverflow.com/questions/7132862/tutorial-for-converting-autotools-to-cmake

Helpful comparison from 
 https://github.com/google/snappy/pull/16/files

Helpful cmake sample at
 https://github.com/snortadmin/snort3/blob/master/cmake/sanity_checks.cmake

CMake manual at
 https://cmake.org/cmake/help/v2.8.8/cmake.html

AutoMake macros at
 https://www.gnu.org/software/automake/manual/html_node/Macro-Index.html

AutoConf macros at
 https://www.gnu.org/savannah-checkouts/gnu/autoconf/manual/autoconf-2.69/html_node/Autoconf-Macro-Index.html

LibTool macros at
 https://www.gnu.org/software/libtool/manual/html_node/Combined-Index.html


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
