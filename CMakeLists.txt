cmake_minimum_required (VERSION 3.13)
project (constexpr-everything CXX)

set(CMAKE_CXX_STANDARD 14)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

set(CMAKE_EXPORT_COMPILE_COMMANDS ON)

find_package(LLVM REQUIRED CONFIG)
message(STATUS "Found LLVM ${LLVM_PACKAGE_VERSION}")
message(STATUS "Using LLVMConfig.cmake in: ${LLVM_DIR}")

add_executable(${PROJECT_NAME} main.cpp)

target_link_libraries(${PROJECT_NAME}
  clangASTMatchers
  clangTooling
  clangDriver
  clangAST
  clangLex
  clangParse
  clangBasic
  clangFrontend
  clangEdit
  clangAST
  clangSerialization
  clangSema
  clangAST
  clangAnalysis
  clangASTMatchers
  clangFrontendTool
  clangDynamicASTMatchers
  clangTooling
  clangAST
  clangASTMatchers
  clangBasic
  clangFrontend
  clangLex
  clangRewrite
  clangRewriteFrontend
  clangTooling
  clangToolingCore
  LLVMTransformUtils
  LLVMAnalysis
  LLVMTarget
  LLVMOption # Support
  LLVMObject # BitReader, Core, Support
  LLVMBitReader # Core, Support
  LLVMCore # Support
  LLVMSupport
)

target_compile_options(${PROJECT_NAME} PUBLIC
  -Wall
  -Wextra
  -Wno-unused-parameter
  -Wshadow
  -fno-exceptions
  -fno-rtti
  -fno-strict-aliasing
  )

target_compile_definitions(${PROJECT_NAME} PUBLIC
  __STDC_LIMIT_MACROS
  __STDC_CONSTANT_MACROS
)
