cmake_minimum_required(VERSION 3.4.3)
project(SimpleProject)

find_package(LLVM REQUIRED CONFIG)

message(STATUS "Found LLVM ${LLVM_PACKAGE_VERSION}")
message(STATUS "Using LLVMConfig.cmake in: ${LLVM_DIR}")

# Set your project compile flags.
# E.g. if using the C++ header files
# you will need to enable C++11 support
# for your compiler.

include_directories(${LLVM_INCLUDE_DIRS})
add_definitions(${LLVM_DEFINITIONS})

# Now build our tools
add_executable(simple-tool tool.cpp)

# Link against LLVM libraries
target_link_libraries(simple-tool 
clangTooling
clangFrontendTool
clangFrontend
clangDriver
clangSerialization
clangCodeGen
clangParse
clangSema
clangStaticAnalyzerFrontend
clangStaticAnalyzerCheckers
clangStaticAnalyzerCore
clangAnalysis
clangARCMigrate
clangRewrite
clangRewriteFrontend
clangEdit
clangAST
clangLex
clangBasic
clang
llvm
version
	)
