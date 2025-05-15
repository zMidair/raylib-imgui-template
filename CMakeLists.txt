cmake_minimum_required(VERSION 4.0)

# project config
set(CMAKE_CXX_STANDARD 20)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_CONFIGURATION_TYPES "Debug;Release")
set_property(DIRECTORY PROPERTY VS_STARTUP_PROJECT "raylib_imgui_template")

project(raylib_imgui_template VERSION 1.0.0)

add_subdirectory(extern/raylib)
add_subdirectory(extern/imgui)

list(APPEND EXTRA_LIBS raylib
                       imgui
                       )
list(APPEND EXTRA_INCLUDES "${PROJECT_SOURCE_DIR}/src"
                           "${PROJECT_SOURCE_DIR}/extern/raylib/src"
                           "${PROJECT_SOURCE_DIR}/extern/imgui/imgui"
                           )

file(GLOB_RECURSE SOURCE_FILES ${PROJECT_SOURCE_DIR}/src/*.cpp ${PROJECT_SOURCE_DIR}/src/*.h)

add_executable(raylib_imgui_template ${SOURCE_FILES})

source_group(TREE ${CMAKE_CURRENT_SOURCE_DIR} FILES ${SOURCE_FILES})

target_link_libraries(raylib_imgui_template PUBLIC ${EXTRA_LIBS})

target_include_directories(raylib_imgui_template PUBLIC ${EXTRA_INCLUDES})
