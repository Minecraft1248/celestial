set (LLVM "E:/llvm-project/llvm")

include_directories ("${LLVM}/include")
link_directories ("${LLVM}/lib")

add_executable (celestial "celestial.cpp" "celestial.h" "ast/ast.h" "codegen/codegen.h" "lex/lex.h" "sema/sema.h" "lex/keyword.h" lex/lex.cpp)

if (CMAKE_VERSION VERSION_GREATER 3.12)
  set_property(TARGET celestial PROPERTY CXX_STANDARD 20)
endif()