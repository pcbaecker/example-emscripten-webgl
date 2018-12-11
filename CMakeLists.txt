cmake_minimum_required(VERSION 3.12)
project(emscripten_webgl)

if("${CMAKE_SYSTEM}" MATCHES "Linux" OR "${CMAKE_SYSTEM}" MATCHES "Darwin-*")

    find_package(OpenGL REQUIRED)

    set(GLFW_BUILD_DOCS OFF CACHE BOOL "" FORCE)
    set(GLFW_BUILD_TESTS OFF CACHE BOOL "" FORCE)
    set(GLFW_BUILD_EXAMPLES OFF CACHE BOOL "" FORCE)
    add_subdirectory(glfw-3.2.1)
endif()

include_directories(glfw-3.2.1/include)
set(CMAKE_CXX_STANDARD 17)

add_executable(emscripten_webgl main.cpp)
target_link_libraries(emscripten_webgl glfw ${OPENGL_LIBRARIES})

if (DEFINED EMSCRIPTEN)
set_target_properties(emscripten_webgl
        PROPERTIES SUFFIX ".html"
        LINK_FLAGS " --bind -s USE_GLFW=3 -s WASM=1 -g4")
endif (DEFINED EMSCRIPTEN)