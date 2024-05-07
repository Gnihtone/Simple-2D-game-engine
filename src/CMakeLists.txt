# CMakeList.txt: проект CMake для src; включите исходный код и определения,
# укажите здесь логику для конкретного проекта.
#
cmake_minimum_required (VERSION 3.20)
find_library(Vulkan vulkan-1 "C:\\VulkanSDK\\1.3.275.0\\Lib")
find_library(GLFW glfw3 "E:\\CAOS\\includes\\glfw-3.4.bin.WIN64\\lib-mingw-w64")

# Включение горячей перезагрузки для компиляторов MSVC, если поддерживается.
if (POLICY CMP0141)
  cmake_policy(SET CMP0141 NEW)
  set(CMAKE_MSVC_DEBUG_INFORMATION_FORMAT "$<IF:$<AND:$<C_COMPILER_ID:MSVC>,$<CXX_COMPILER_ID:MSVC>>,$<$<CONFIG:Debug,RelWithDebInfo>:EditAndContinue>,$<$<CONFIG:Debug,RelWithDebInfo>:ProgramDatabase>>")
endif()

project ("src")

# Добавьте источник в исполняемый файл этого проекта.
add_executable (src "src.cpp" "src.h")

if (CMAKE_VERSION VERSION_GREATER 3.12)
  set_property(TARGET src PROPERTY CXX_STANDARD 20)
endif()
target_include_directories(src PUBLIC "C:\\VulkanSDK\\1.3.275.0\\Include")
target_include_directories(src PUBLIC "E:\\CAOS\\includes\\glfw-3.4.bin.WIN64\\include")
target_include_directories(src PUBLIC "E:\\CAOS\\includes\\glm")

target_link_libraries(src PRIVATE "${Vulkan}")
target_link_libraries(src PRIVATE "${GLFW}")

# TODO: Добавьте тесты и целевые объекты, если это необходимо.
