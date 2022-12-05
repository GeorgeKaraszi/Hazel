set(PROJECT_NAME ImGuizmo)
project(${PROJECT_NAME})

set(PROJ_LIBS ImGui)

file(GLOB SRC_FILES ${CMAKE_CURRENT_SOURCE_DIR}/*.cpp)



add_library(${PROJECT_NAME} ${SRC_FILES})
target_link_libraries(${PROJECT_NAME} ${PROJ_LIBS})
set_target_properties(${PROJECT_NAME} PROPERTIES INTERFACE_INCLUDE_DIRECTORIES ${CMAKE_CURRENT_SOURCE_DIR})

#target_include_directories(${PROJECT_NAME} PUBLIC "../imgui")
