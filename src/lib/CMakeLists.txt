message(STATUS "Starting src/lib/CMakeLists.txt")

add_definitions(-DHAVE_CONFIG_H)
add_library(hesiod SHARED
    hesiod.c
    hesmailhost.c
    hespwnam.c
    hesservbyname.c
    hescompat.c)
