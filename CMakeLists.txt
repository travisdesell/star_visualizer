cmake_minimum_required (VERSION 2.6)
project (TEST_RANDOM)

# The version number.
set (TEST_RANDOM_VERSION_MAJOR 1)
set (TEST_RANDOM_VERSION_MINOR 0)

# These will make cmake use clang and clang++ instead of gcc and g++
#SET (CMAKE_C_COMPILER             "/usr/bin/clang")
SET (CMAKE_C_FLAGS                "-Wall -std=c99")
SET (CMAKE_C_FLAGS_DEBUG          "-g")
SET (CMAKE_C_FLAGS_MINSIZEREL     "-Os -DNDEBUG")
SET (CMAKE_C_FLAGS_RELEASE        "-O4 -DNDEBUG")
SET (CMAKE_C_FLAGS_RELWITHDEBINFO "-O2 -g")

#looks like on OSX the c++ clang compiler is also clang, not clang++
#SET (CMAKE_CXX_COMPILER             "/usr/bin/clang")
#SET (CMAKE_CXX_COMPILER             "/opt/local/bin/clang++-mp-3.1")
SET (CMAKE_CXX_FLAGS                "-Wall")
SET (CMAKE_CXX_FLAGS_DEBUG          "-g")
SET (CMAKE_CXX_FLAGS_MINSIZEREL     "-Os -DNDEBUG")
SET (CMAKE_CXX_FLAGS_RELEASE        "-O4 -DNDEBUG")
SET (CMAKE_CXX_FLAGS_RELWITHDEBINFO "-O2 -g")

SET (CMAKE_AR      "/usr/bin/llvm-ar")
SET (CMAKE_LINKER  "/usr/bin/llvm-ld")
SET (CMAKE_NM      "/usr/bin/llvm-nm")
SET (CMAKE_OBJDUMP "/usr/bin/llvm-objdump")
SET (CMAKE_RANLIB  "/usr/bin/llvm-ranlib")

set(CMAKE_LIBRARY_PATH ${CMAKE_LIBRARY_PATH} /opt/local/lib)

find_package(Boost REQUIRED COMPONENTS system)
find_package(OpenGL REQUIRED)
find_package(GLUT REQUIRED)

include_directories(${Boost_INCLUDE_DIR} ${OPENGL_INCLUDE_DIRS} ${GLUT_INCLUDE_DIRS})
link_directories(${Boost_LIBRARY_DIRS} ${OPENGL_LIBRARY_DIRS} ${GLUT_LIBRARY_DIRS})

add_executable(star_visualizer star_visualizer)
target_link_libraries(star_visualizer ${OPENGL_LIBRARIES} ${GLUT_LIBRARIES} ${Boost_SYSTEM_LIBRARY})
