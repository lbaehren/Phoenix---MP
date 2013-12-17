## =============================================================================
##
##  CMake projects settings
##
## =============================================================================

## Name of the project
project (Phoenix++)

## Minimum required version of CMake to configure the project
cmake_minimum_required(VERSION 2.8)

## Set various version numbers
set (PROJECT_VERSION_MAJOR "1")
set (PROJECT_VERSION_MINOR "0")
set (PROJECT_VERSION_PATCH "1")

set (PROJECT_VERSION_SERIES "${PROJECT_VERSION_MAJOR}.${PROJECT_VERSION_MINOR}")
set (PROJECT_VERSION "${PROJECT_VERSION_SERIES}.${PROJECT_VERSION_PATCH}")

## CMake standard modules
include (CheckIncludeFile)
include (CheckFunctionExists)
include (CheckTypeSize)
include (FindPackageHandleStandardArgs)

## =============================================================================
##
##  Configuration options
##
## =============================================================================

option (BUILD_SHARED_LIBS  "Enable building shared libraries?"                      YES )
option (WITH_TESTS         "Enable the CTest test driver and build test programs?"  NO  )
option (WITH_DOCUMENTATION "Build source code and extended documentation?"          NO  )

##__________________________________________________________
## Handle option: Enable building shared libraries?

if (BUILD_SHARED_LIBS)
    add_definitions (-fPIC -O3)
endif ()

## =============================================================================
##
##  System inspection
##
## =============================================================================

## =============================================================================
##
##  Project configuration
##
## =============================================================================


if (APPLE)
    add_definitions (-D_DARWIN_)
#    DEBUG = -g
#    CFLAGS = $(DEBUG) -Wall -O3 $(OS)
#    LIBS = -lpthread
endif (APPLE)

include_directories (
    ${PROJECT_SOURCE_DIR}/include
    )

add_subdirectory (src)

## =============================================================================
##
##  Configuration summary
##
## =============================================================================

message ( " ========================================================"     )
message ( " [Phoenix++] Configuration summary"                            )
message ( " --------------------------------------------------------"     )
message ( " System configuration"                                         )
message ( " .. Processor type .............. = ${CMAKE_SYSTEM_PROCESSOR}" )
message ( " .. CMake executable ............ = ${CMAKE_COMMAND}"          )
message ( " .. CMake version ............... = ${CMAKE_VERSION}"          )
message ( " .. System name ................. = ${CMAKE_SYSTEM_NAME}"      )
message ( " .. System version .............. = ${CMAKE_SYSTEM_VERSION}"   )
message ( " .. C compiler .................. = ${CMAKE_C_COMPILER}"       )
message ( " .. C compiler flags ............ = ${CMAKE_C_FLAGS}"          )
message ( " .. C++ compiler ................ = ${CMAKE_CXX_COMPILER}"     )
message ( " .. C++ compiler flags .......... = ${CMAKE_CXX_FLAGS}"        )
message ( " .. Memory checker .............. = ${MEMORYCHECK_COMMAND}"    )
message ( " ========================================================"     )

