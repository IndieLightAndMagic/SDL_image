#CMAKE TO MAKE A STATIC LIBRARY
#HEADER
cmake_minimum_required(VERSION 3.9.0 FATAL_ERROR)
set(TARGET_NAME SDL_image)
project(${TARGET_NAME})
set(CMAKE_VERBOSE_MAKEFILE TRUE)
set(CMAKE_CXX_STANDARD 17)

#Installation directory 
get_filename_component(GTECH_DIR $ENV{GTECH_ROOT} ABSOLUTE)
set(GTECH_DIR_LIB ${GTECH_DIR}/3rd/lib/)
set(GTECH_DIR_INC ${GTECH_DIR}/3rd/include/SDLWrapper)

#DIRECTORIES
get_filename_component(ROOT_DIR "." ABSOLUTE)
message(STATUS "-----------------------------")
message(STATUS "SYSTEM NAME: ${CMAKE_SYSTEM_NAME}")
message(STATUS "ROOT_DIR: ${ROOT_DIR}")
message(STATUS "CMAKE_SOURCE_DIR: ${CMAKE_SOURCE_DIR}")
message(STATUS "CMAKE_CURRENT_BINARY_DIR: ${CMAKE_CURRENT_BINARY_DIR}")
message(STATUS "-----------------------------")

#SDL
set(SDL2_DIR ${CMAKE_SOURCE_DIR}/../SDL/include)

add_library(${TARGET_NAME} STATIC
    ${CMAKE_SOURCE_DIR}/sdlwrapper.cpp 
)
target_link_libraries(${TARGET_NAME} PUBLIC ${CMAKE_SOURCE_DIR}/../SDL/m/libSDL2.a)

set(INC_DIR_SET 
	${SDL2_DIR}
)

target_include_directories(${TARGET_NAME} PUBLIC 
	${INC_DIR_SET}    
)
message(STATUS "-----------------------------")
message(STATUS "INCLUDE_DIRECTORIES: ${INC_DIR_SET}")
message(STATUS "-----------------------------")


