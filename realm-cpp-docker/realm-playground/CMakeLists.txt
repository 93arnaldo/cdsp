cmake_minimum_required(VERSION 3.15)

project (realm_helloworld)

set(CMAKE_CXX_STANDARD 17)

set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS}")

find_library(REALM_CPP_LIB NAMES cpprealm)
find_library(REALM_OS_LIB NAMES realm-object-store)
find_library(REALM_SYNC_LIB NAMES realm-sync)
find_library(REALM_LIB NAMES realm)
find_library(REALM_PARSER_LIB NAMES realm-parser)
include_directories(/usr/local/include/ )
link_directories(/usr/local/bin/)

add_executable(realm_cpp_app main.cpp)

target_link_libraries(realm_cpp_app ${REALM_CPP_LIB} ${REALM_OS_LIB} ${REALM_SYNC_LIB} ${REALM_LIB} ${REALM_PARSER_LIB} z curl uv ssl crypto)