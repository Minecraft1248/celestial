cmake_minimum_required (VERSION 3.8)

project ("celestial")

set (LLVM "E:/llvm-project/build/")

include_directories ("${LLVM}/include")
link_directories ("${LLVM}/lib")

add_subdirectory ("celestial")
