message(STATUS "Starting src/hesinfo/CMakeLists.txt")

include_directories("../lib")

add_executable(hesinfo
    hesinfo.c)

target_link_libraries(hesinfo LINK_PUBLIC hesiod)