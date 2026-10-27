cmake_minimum_required(VERSION 3.21)
project(apprentice VERSION 1.1.0 LANGUAGES CXX)

find_package(CommonLibSSE CONFIG REQUIRED)
find_package(nlohmann_json CONFIG REQUIRED)

file(GLOB sources CONFIGURE_DEPENDS src/*.cpp)
add_commonlibsse_plugin(${PROJECT_NAME} AUTHOR lambdacdm SOURCES ${sources})
target_compile_features(${PROJECT_NAME} PRIVATE cxx_std_23)
target_include_directories(${PROJECT_NAME} PRIVATE include)
target_precompile_headers(${PROJECT_NAME} PRIVATE include/pch.h)
target_link_libraries(${PROJECT_NAME} PRIVATE nlohmann_json::nlohmann_json)
