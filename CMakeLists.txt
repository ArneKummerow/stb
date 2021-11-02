# === CMAKE ====================================================================

# Version
cmake_minimum_required(VERSION 3.14.0)

# Includes
include(cmake/PreCMakeLists.cmake)

# Target
set(TARGET stb)
set(TARGET_LIST ${TARGET_LIST} ${TARGET})
project(${TARGET} VERSION 1.0.0)
add_library(${TARGET})

# === OPTION ===================================================================

# === TOOL =====================================================================

# C/C++ Standard
set(CMAKE_C_STANDARD 99)
set(CMAKE_CXX_STANDARD 17)

# Compile flags
# target_compile_definitions(${TARGET}
# )

# === FILE =====================================================================

# Directories
set(${TARGET}_SOURCE_DIR ${CMAKE_CURRENT_LIST_DIR}/src)
set(${TARGET}_INCLUDE_DIR ${CMAKE_CURRENT_LIST_DIR})
set(${TARGET}_EXTERNAL_DIR ${CMAKE_CURRENT_LIST_DIR}/external)

# Sources
target_sources(${TARGET}
    PRIVATE
    ${${TARGET}_SOURCE_DIR}/stb_image.cpp
)

# Public headers
set(${TARGET}_PUBLIC_HEADERS
    ${${TARGET}_INCLUDE_DIR}/stb_image.h
)

# Include directories
target_include_directories(${TARGET}
    PUBLIC
    $<INSTALL_INTERFACE:include>

    PRIVATE
    ${${TARGET}_INCLUDE_DIR}
    ${${TARGET}_SOURCE_DIR}
    ${${TARGET}_EXTERNAL_DIR}
    ${CMAKE_BINARY_DIR}
)

# === DEPENDENCY ===============================================================

# Dependencies
# target_link_libraries(${TARGET}
# )

# === CMAKE ====================================================================

include(cmake/PublicHeader.cmake)
include(cmake/ConfigHeader.cmake)
include(cmake/Install.cmake)
include(cmake/PackageConfig.cmake)