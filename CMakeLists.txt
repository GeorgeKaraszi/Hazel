cmake_minimum_required(VERSION 3.23)
project(HazelApplication)

set(CMAKE_CXX_STANDARD 20)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_CXX_EXTENSIONS OFF)

include("cmake/conan.cmake")

conan_cmake_run(
        CONANFILE conanfile.txt
        BASIC_SETUP CMAKE_TARGETS
        BUILD missing
)

add_subdirectory(Hazel/vendor/imgui)
add_subdirectory(Hazel/vendor/ImGuizmo)
add_subdirectory(Hazel/vendor/stb_image)
add_subdirectory(Hazel)
add_subdirectory(Hazelnut)
add_subdirectory(Sandbox)
