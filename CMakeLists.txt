# CMakeList.txt: 顶层 CMake 项目文件，在此处执行全局配置
# 并包含子项目。
#
cmake_minimum_required (VERSION 3.8)

project ("temprepos")

set (LLVM "E:/llvm-project/llvm")

include_directories ("${LLVM}/include")
link_directories ("${LLVM}/lib")

link_libraries ("LLVMJIT.lib" "LLVMX86CodeGen.lib" "LLVMExecutionEngine.lib" "LLVMAsmPrinter.lib" "LLVMSelectionDAG.lib" "LLVMX86Desc.lib" "LLVMMCParser.lib" "LLVMCodeGen.lib" "LLVMX86AsmPrinter.lib" "LLVMX86Info.lib" "LLVMScalarOpts.lib" "LLVMX86Utils.lib" "LLVMInstCombine.lib" "LLVMTransformUtils.lib" "LLVMipa.lib" "LLVMAnalysis.lib" "LLVMTarget.lib" "LLVMCore.lib" "LLVMMC.lib" "LLVMObject.lib" "LLVMSupport.lib")

# 包含子项目。
add_subdirectory ("temprepos")
