# clang-tools-test
A test for building LibTooling sample using [LibTool documentation](https://clang.llvm.org/docs/LibTooling.html).

# Builds on
- mingw64 using MSYS2

# Dependacies
- llvm-devel
- clang-devel

# Why
I created this because I needed a sample to build clang Libtool projects out of the LLVM source tree, which mind you is huge and can take time to build on slower machines.


The documentation on clang LibTool is serverly lacking when it comes to building out of tree because it doesn't list what libraries, and what order you need them in. 

There are several stackoverflow posts such as [this one](https://stackoverflow.com/questions/21692934/linking-against-clang-llvm-libraries-on-linux-always-fails) that have people failing to build clang because of the library order.

# What
I believe the source code is basically what [clang-check](https://clang.llvm.org/docs/ClangCheck.html) does and has some of the same options.

# How
Run `cmake` in your build enviroment with clang and llvm libraries installed.

Sample for mingw64 in MSYS2: `cmake -G "Unix Makefiles" -DCMAKE_EXPORT_COMPILE_COMMANDS=1 ..`

# Running executable
```./simple-tool.exe -p="./" ../tool.cpp -- -I/include -std=c++11```

## Variables
- `-p` is the directory of the build database, in this case, CMake's json database (compile_commands.json).
- `../tool.cpp` is the source file to check
- `--` is where you list the build commands after
- `-I/include` is your system's include directory, add more for all your header directories, can be relative
- `-std=c++11` tell it to use c++ 11 standard


# The LibTooling library order is
- clangTooling
- clangFrontendTool
- clangFrontend
- clangDriver
- clangSerialization
- clangCodeGen
- clangParse
- clangSema
- clangStaticAnalyzerFrontend
- clangStaticAnalyzerCheckers
- clangStaticAnalyzerCore
- clangAnalysis
- clangARCMigrate
- clangRewrite
- clangRewriteFrontend
- clangEdit
- clangAST
- clangLex
- clangBasic
- clang
- llvm
- version # You only need this if you're building for windows
