#CMAKE TO MAKE A STATIC LIBRARY
#HEADER
cmake_minimum_required(VERSION 3.9.0 FATAL_ERROR)
set(TARGET_NAME SDL_image)
project(${TARGET_NAME})

set(CMAKE_C_COMPILER "/usr/bin/clang")
set(CMAKE_VERBOSE_MAKEFILE TRUE)
set(CMAKE_CXX_STANDARD 17)


#DIRECTORIES
get_filename_component(ROOT_DIR "." ABSOLUTE)
message(STATUS "-----------------------------")
message(STATUS "SYSTEM NAME: ${CMAKE_SYSTEM_NAME}")
message(STATUS "ROOT_DIR: ${ROOT_DIR}")
message(STATUS "CMAKE_SOURCE_DIR: ${CMAKE_SOURCE_DIR}")
message(STATUS "CMAKE_CURRENT_BINARY_DIR: ${CMAKE_CURRENT_BINARY_DIR}")

if ("$ENV{XCODE_SDK_PLATFORM}" STREQUAL "")
	message(FATAL_ERROR "XCODE_SDK_PLATFORM environment variable is not defined, run xcrun --show-sdk-path and export the result.")
else()
	message(STATUS "XCODE_SDK_PLATFORM: $ENV{XCODE_SDK_PLATFORM}")
endif()
message(STATUS "-----------------------------")

#SDL
set(SDL2_DIR $ENV{GTECH_ROOT}/3rd/include/SDL2)
set(CMAKE_C_FLAGS "-x objective-c -arch x86_64 -fmessage-length=0 -fdiagnostics-show-note-include-stack -fmacro-backtrace-limit=0 -Wno-trigraphs -fpascal-strings -O0 -Wno-missing-field-initializers -Wno-missing-prototypes -Wno-return-type -Wno-missing-braces -Wparentheses -Wswitch -Wno-unused-function -Wno-unused-label -Wno-unused-parameter -Wno-unused-variable -Wunused-value -Wno-empty-body -Wno-uninitialized -Wno-unknown-pragmas -Wno-shadow -Wno-four-char-constants -Wno-conversion -Wno-constant-conversion -Wno-int-conversion -Wno-bool-conversion -Wno-enum-conversion -Wno-float-conversion -Wno-non-literal-null-conversion -Wno-objc-literal-conversion -Wno-shorten-64-to-32 -Wpointer-sign -Wno-newline-eof -isysroot $ENV{XCODE_SDK_PLATFORM}
	-fasm-blocks -fstrict-aliasing -Wdeprecated-declarations -mmacosx-version-min=10.6 -g -fvisibility=hidden -Wno-sign-conversion -Wno-infinite-recursion -Wno-comma -Wno-block-capture-autoreleasing -Wno-strict-prototypes -Wno-semicolon-before-method-body -MMD")
add_library(${TARGET_NAME} STATIC
	${CMAKE_SOURCE_DIR}/IMG.c
	${CMAKE_SOURCE_DIR}/IMG_ImageIO.m
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
add_definitions(
	-DLOAD_BMP
	-DLOAD_GIF 
	-DLOAD_JPG 
	-DLOAD_LBM 
	-DLOAD_PCX 
	-DLOAD_PNG 
	-DLOAD_PNM 
	-DLOAD_SVG 
	-DLOAD_TGA 
	-DLOAD_TIF 
	-DLOAD_WEBP 
	-DLOAD_XPM 
	-DLOAD_XV
	)

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


