cmake_minimum_required(VERSION 3.0)

message(STATUS "Starting top CMakeLists.txt")

project(hesiod C)

include(CheckIncludeFiles)
include(CheckLibraryExists)

# Set options with "-D" before naming the source path:
# cmake -DWITH_LIBIDN=OFF ..
option(WITH_LIBIDN "Use libidn" ON)
if (WITH_LIBIDN)
  check_library_exists(idn stringprep_check_version "" HAVE_LIBIDN)
endif(WITH_LIBIDN)
# Todo: test with libidn.  Test with libidn-headers

check_library_exists(resolv res_mkquery "" HAVE_LIBRESOLV)

# AC_HEADER_RESOLV
check_include_files("sys/types.h" HAVE_SYS_TYPES_H)
check_include_files("netinet/in.h" HAVE_NETINET_IN_H)
check_include_files("arpa/nameser.h" HAVE_ARPA_NAMESER_H)
check_include_files("netdb.h" HAVE_NETDB_H)
check_include_files("resolv.h" HAVE_RESOLV_H)

check_include_files("stdlib.h" HAVE_STDLIB_H)
check_include_files("string.h" HAVE_STRING_H)
check_include_files("sys/socket.h" HAVE_SYS_SOCKET_H)

# UNCONVERTED AUTOTOOL OPTIONS

#AC_TYPE_SSIZE_T
#AC_TYPE_UID_T

include(CheckStructHasMember)

check_struct_has_member("struct passwd" pw_quota pwd.h HAVE_PW_QUOTA LANGUAGE C)
check_struct_has_member("struct passwd" pw_comment pwd.h HAVE_PW_COMMENT LANGUAGE C)
check_struct_has_member("struct passwd" pw_class pwd.h HAVE_PW_CLASS LANGUAGE C)
check_struct_has_member("struct passwd" pw_change pwd.h HAVE_PW_CHANGE LANGUAGE C)
check_struct_has_member("struct passwd" pw_expire pwd.h HAVE_PW_EXPIRE LANGUAGE C)

# UNCONVERTED AUTOTOOL OPTIONS

#AC_FUNC_MALLOC
#AC_FUNC_REALLOC

include(CheckFunctionExists)

check_function_exists(strchr HAVE_STRCHR)
check_function_exists(strdup HAVE_STRDUP)
check_function_exists(secure_getenv HAVE_SECURE_GETENV)

message(STATUS "Writing config.h")
configure_file (${CMAKE_CURRENT_SOURCE_DIR}/config.h.cmake ${CMAKE_CURRENT_BINARY_DIR}/config.h)

add_subdirectory(src)
add_subdirectory(man)

message(STATUS "Ending top CMakeLists.txt")
