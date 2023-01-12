# CMakeList.txt: temprepos 的 CMake 项目，在此处包括源代码并定义
# 项目特定的逻辑。
#

# 将源代码添加到此项目的可执行文件。

set (LLVM "E:/llvm-project/llvm")

include_directories ("${LLVM}/include")
link_directories ("${LLVM}/lib")

add_executable (temprepos "temprepos.cpp" "temprepos.h" "ast/ast.h" "codegen/codegen.h" "lex/lex.h" "sema/sema.h")

if (CMAKE_VERSION VERSION_GREATER 3.12)
  set_property(TARGET temprepos PROPERTY CXX_STANDARD 20)
endif()

# TODO: 如有需要，请添加测试并安装目标。
