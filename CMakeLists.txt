cmake_minimum_required(VERSION 3.26...3.29)

set(CMAKE_C_STANDARD 11)
set(CMAKE_CXX_STANDARD 20)

project(HelloLuisa VERSION 0.1.0 LANGUAGES C CXX)

include(CMakeOptions.cmake)

# you may set the LUISA_COMPUTE_ENABLE_XXX options before including LuisaCompute
add_subdirectory(ext/LuisaCompute)

# setup the output directories to make the executables under the same binary directory as LuisaCompute
include(ext/LuisaCompute/scripts/setup_output_dirs.cmake)

# add your executables
set(EXECUTE_NAME HelloLuisa)

add_subdirectory(src)
target_link_libraries(${EXECUTE_NAME} PRIVATE luisa::compute)
