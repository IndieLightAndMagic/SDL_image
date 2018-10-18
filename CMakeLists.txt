#CMAKE TO MAKE A STATIC LIBRARY
#HEADER
cmake_minimum_required(VERSION 3.9.0 FATAL_ERROR)
set(TARGET_NAME SDL_image)
project(${TARGET_NAME})
set(CMAKE_VERBOSE_MAKEFILE TRUE)
set(CMAKE_CXX_STANDARD 17)


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
	${CMAKE_SOURCE_DIR}/IMG.c
	${CMAKE_SOURCE_DIR}/IMG_WIC.c
	${CMAKE_SOURCE_DIR}/IMG_bmp.c
	${CMAKE_SOURCE_DIR}/IMG_gif.c
	${CMAKE_SOURCE_DIR}/IMG_jpg.c
	${CMAKE_SOURCE_DIR}/IMG_lbm.c
	${CMAKE_SOURCE_DIR}/IMG_pcx.c
	${CMAKE_SOURCE_DIR}/IMG_png.c
	${CMAKE_SOURCE_DIR}/IMG_pnm.c
	${CMAKE_SOURCE_DIR}/IMG_svg.c
	${CMAKE_SOURCE_DIR}/IMG_tga.c
	${CMAKE_SOURCE_DIR}/IMG_tif.c
	${CMAKE_SOURCE_DIR}/IMG_webp.c
	${CMAKE_SOURCE_DIR}/IMG_xcf.c
	${CMAKE_SOURCE_DIR}/IMG_xpm.c
	${CMAKE_SOURCE_DIR}/IMG_xv.c
	${CMAKE_SOURCE_DIR}/IMG_xxx.c
	${CMAKE_SOURCE_DIR}/showimage.c 
)
target_link_libraries(${TARGET_NAME} PUBLIC ${CMAKE_SOURCE_DIR}/../SDL/m/libSDL2.a)

set(INC_DIR_SET 
	${SDL2_DIR}
	${CMAKE_SOURCE_DIR}
)

target_include_directories(${TARGET_NAME} PUBLIC 
	${INC_DIR_SET}    
)
message(STATUS "-----------------------------")
message(STATUS "INCLUDE_DIRECTORIES: ${INC_DIR_SET}")
message(STATUS "-----------------------------")


