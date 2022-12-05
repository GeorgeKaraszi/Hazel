set(PROJECT_NAME Hazel)
project(${PROJECT_NAME})

find_package(Vulkan REQUIRED)

set(PROJ_LIBS
        CONAN_PKG::glad
        CONAN_PKG::glfw
        CONAN_PKG::glm
        CONAN_PKG::glew
        CONAN_PKG::stb
        CONAN_PKG::sdl
        CONAN_PKG::spdlog
        CONAN_PKG::box2d
        CONAN_PKG::yaml-cpp
        ImGui
        ImGuizmo
        Vulkan::shaderc_combined
        Vulkan::glslang
        Vulkan::SPIRV-Tools
        Vulkan::Headers
        )


file(GLOB_RECURSE PROJ_SRC LIST_DIRECTORIES false src/*.cpp)

include_directories(${CMAKE_CURRENT_SOURCE_DIR}/src)
include_directories(${CMAKE_CURRENT_SOURCE_DIR}/vendor/entt/include)
include_directories(${CMAKE_CURRENT_SOURCE_DIR}/vendor/mono/include)
include_directories(${CMAKE_CURRENT_SOURCE_DIR}/vendor/filewatch)
include_directories(${VULKAN_INCLUDE_DIRS})

add_library(${PROJECT_NAME} STATIC ${PROJ_SRC})
target_precompile_headers(${PROJECT_NAME} PRIVATE src/hzpch.h)

target_link_libraries(${PROJECT_NAME} ${PROJ_LIBS})
