set(PROJECT_NAME Hazelnut)
project(${PROJECT_NAME})

set(PROJ_LIBS Hazel)

file(GLOB_RECURSE PROJ_SRC LIST_DIRECTORIES false src/*.cpp)

add_executable(${PROJECT_NAME} ${PROJ_SRC})
add_dependencies(${PROJECT_NAME} Hazel)
target_link_libraries(${PROJECT_NAME} PRIVATE ${PROJ_LIBS})
