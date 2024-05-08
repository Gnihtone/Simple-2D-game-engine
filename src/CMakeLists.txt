cmake_minimum_required (VERSION 3.20)
find_library(Vulkan vulkan "/usr/local/lib")
find_library(GLFW glfw3 "/opt/homebrew/Cellar/glfw/3.4/lib")

project ("src")

add_executable (src "src.cpp" "src.h")

set_property(TARGET src PROPERTY CXX_STANDARD 20)
set(CMAKE_CXX_FLAGS "-framework Cocoa -framework OpenGL -framework IOKit -framework CoreVideo")

target_include_directories(src PUBLIC "/usr/local/include")
target_include_directories(src PUBLIC "/opt/homebrew/Cellar/glfw/3.4/include")

target_link_libraries(src PRIVATE "${Vulkan}")
target_link_libraries(src PRIVATE "${GLFW}")

add_definitions(-D__APPLE__)