set(PROJECT_NAME Hazel)
project(${PROJECT_NAME})

find_package(Vulkan REQUIRED)
find_library(Mono_LIB mono libmono libmono-static-sgen HINTS ${CMAKE_CURRENT_SOURCE_DIR}/vendor/mono REQUIRED)

set(PROJ_LIBS
        wsock32
        ws2_32
        bcrypt
        CONAN_PKG::glad
        CONAN_PKG::glfw
        CONAN_PKG::glm
        CONAN_PKG::glew
        CONAN_PKG::sdl
        CONAN_PKG::spdlog
        CONAN_PKG::box2d
        CONAN_PKG::yaml-cpp
        CONAN_PKG::spirv-cross
        Vulkan::shaderc_combined
        Vulkan::glslang
        Vulkan::Headers
        ImGui
        ImGuizmo
        stb_image
        ${Mono_LIB}
        )


file(GLOB_RECURSE PROJ_SRC LIST_DIRECTORIES false src/*.cpp)


add_library(${PROJECT_NAME} STATIC ${PROJ_SRC})
target_precompile_headers(${PROJECT_NAME} PRIVATE src/hzpch.h)

target_include_directories(${PROJECT_NAME}
        PUBLIC "${CMAKE_CURRENT_SOURCE_DIR}/src"
        PUBLIC "${CMAKE_CURRENT_SOURCE_DIR}/vendor/entt/include;"
        PUBLIC "${CMAKE_CURRENT_SOURCE_DIR}/vendor/mono/include;"
        PUBLIC "${CMAKE_CURRENT_SOURCE_DIR}/vendor/filewatch;"
        PUBLIC "${VULKAN_INCLUDE_DIRS}"
        )

target_link_libraries(${PROJECT_NAME} ${PROJ_LIBS})
