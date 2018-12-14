# Created by the script cgal_create_cmake_script_with_options
# This is the CMake script for compiling a set of CGAL applications.

project( parser_test )

CMAKE_MINIMUM_REQUIRED(VERSION 2.4.5)

set( CMAKE_ALLOW_LOOSE_LOOP_CONSTRUCTS true )
 
if ( COMMAND cmake_policy )

  cmake_policy( SET CMP0003 NEW )  

endif()

# NOTE NOTE: it is important that Qt3 linker flags appear *after* CUDA
# libraries otherwise runtime crash
# CGAL and its components
find_package( CGAL REQUIRED COMPONENTS Core )

if ( NOT CGAL_FOUND )
  message(STATUS "This project requires the CGAL library, and will not be compiled.")
  return()  
endif()

# include helper file
include( ${CGAL_USE_FILE} )

find_package( MPFI )
if ( MPFI_FOUND )
 include( ${MPFI_USE_FILE} )
else()
  message(STATUS "This project requires the MPFI library, and will not be compiled.")
  return()
endif( MPFI_FOUND ) 

find_package( RS )
if ( RS_FOUND )
 include( ${RS_USE_FILE} )
else()
  message(STATUS "This project requires the RS library, and will not be compiled.")
  return()
endif( RS_FOUND )   

add_executable( parser_test1 default_parser_policy.cpp )
add_executable( parser_test2 mixed_rational_parser_policy.cpp )
add_executable( parser_test3 mixed_floating_point_parser_policy.cpp )
add_executable( parser_test4 Polynomial_parser_d_advanced.cpp )

add_to_cached_list( CGAL_EXECUTABLE_TARGETS parser_test )

link_libraries( ${Boost_THREAD_LIBRARY} "$ENV{HOME}/thirdparty_libs/ntl32/lib/libntl.a")
