cmake_minimum_required(VERSION 2.8)
project( fontconfig )
set( CMAKE_MODULE_PATH ${CMAKE_SOURCE_DIR}/cmake/modules )

find_package( EXPAT REQUIRED )
find_package( Freetype REQUIRED )

include_directories(
    ${EXPAT_INCLUDE_DIR}
    ${FREETYPE_INCLUDE_DIRS}
    ${CMAKE_INCLUDE_PATH}
    ${CMAKE_CURRENT_BINARY_DIR}
    ${CMAKE_CURRENT_SOURCE_DIR}
    ${CMAKE_CURRENT_SOURCE_DIR}/src
)

if( MSVC )
    include_directories( ${CMAKE_INCLUDE_PATH}/msvc )
    add_definitions( -D_CRT_SECURE_NO_DEPRECATE -D_CRT_NONSTDC_NO_DEPRECATE -wd4018)
endif(MSVC)
link_directories( ${CMAKE_LIBRARY_PATH} )

include( ConfigureChecks.cmake )

add_subdirectory( fontconfig )
add_subdirectory( src )

add_subdirectory( conf.d )
