# --------------------------------------------------------------------------- #
# Author:       Joey Dumont                   <joey.dumont@gmail.com>         #
# Date:         2015-02-26                                                    #
# Description:  GPLv3			                                      #
# ----------------------------------------------------------------------------#

# ----------------------------------------------------------------- #
# --                 Name and version of library                 -- #
# ----------------------------------------------------------------- #
project(Cubature)
set (Cubature_VERSION_MAJOR 1)
set (Cubature_VERSION_MINOR 0)
set (Cubature_VERSION_RELEASE 2)

# ----------------------------------------------------------------- #
# --               Configuration and Dependencies                -- #
# ----------------------------------------------------------------- #
# -- CMake version and installation directory.
cmake_minimum_required(VERSION 2.8)
if (CMAKE_INSTALL_PREFIX_INITIALIZED_TO_DEFAULT)
    set (CMAKE_INSTALL_PREFIX /usr)
endif()

# ----------------------------------------------------------------- #
# --                  Compilation Instructions                   -- #
# ----------------------------------------------------------------- #
# -- Included files
include_directories(${CMAKE_CURRENT_SOURCE_DIR}/include INC_LIST)

# -- Source files
aux_source_directory(${CMAKE_CURRENT_SOURCE_DIR}/src SRC_LIST)
list(REMOVE_ITEM SRC_LIST ${CMAKE_CURRENT_SOURCE_DIR}/src/clencurt_gen.c)

# -- Build a shared library.
add_library(${PROJECT_NAME} STATIC ${SRC_LIST})


# -- Define the properties of the library to be built.
set_target_properties(
  ${PROJECT_NAME}
  PROPERTIES
    VERSION ${Cubature_VERSION_MAJOR}.${Cubature_VERSION_MINOR}.${Cubature_VERSION_RELEASE}
    SOVERSION ${Cubature_VERSION_MAJOR}.${Cubature_VERSION_MINOR}.${Cubature_VERSION_RELEASE}
)

# -- Instalation directories
install (TARGETS ${PROJECT_NAME} DESTINATION lib)
install (DIRECTORY include/ DESTINATION include)
    
    
