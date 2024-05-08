cmake_minimum_required (VERSION 3.20)
find_library(Vulkan vulkan-1 "C:\\VulkanSDK\\1.3.275.0\\Lib")
find_library(GLFW glfw3 "E:\\CAOS\\includes\\glfw-3.4.bin.WIN64\\lib-mingw-w64")

project ("src")

add_executable (src "src.cpp" "src.h")

set_property(TARGET src PROPERTY CXX_STANDARD 20)

target_include_directories(src PUBLIC "C:\\VulkanSDK\\1.3.275.0\\Include")
target_include_directories(src PUBLIC "E:\\CAOS\\includes\\glfw-3.4.bin.WIN64\\include")
target_include_directories(src PUBLIC "E:\\CAOS\\includes\\glm")

target_link_libraries(src PRIVATE "${Vulkan}")
target_link_libraries(src PRIVATE "${GLFW}")
