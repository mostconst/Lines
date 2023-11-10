cmake_minimum_required( VERSION 2.8 )

project( lines )

set(CMAKE_MODULE_PATH ${CMAKE_MODULE_PATH} "${CMAKE_SOURCE_DIR}/cmake/")

if(WIN32)
	set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${CMAKE_SOURCE_DIR}/bin)
endif(WIN32)

find_package( OpenGL REQUIRED )
option(GLFW_BUILD_DOCS OFF)
option(GLFW_BUILD_EXAMPLES OFF)
option(GLFW_BUILD_TESTS OFF)
add_subdirectory(extern/glfw)

include_directories( "${CMAKE_SOURCE_DIR}" "${CMAKE_SOURCE_DIR}/extern" )

add_executable( lines main.c extern/glad.c )
target_link_libraries( lines glfw ${OPENGL_gl_LIBRARY} )
target_include_directories(lines PRIVATE extern/glfw/include)
#target_compile_options( lines PRIVATE -std=c11 -Wall )