# Solution configuration

cmake_minimum_required(VERSION 4.2.1)
project(projects VERSION 1.0.1 LANGUAGES CXX)

set(PROJECT_VERSION_PRERELEASE_IDENTIFIER)
set(PROJECT_VERSION_PRERELEASE_PATCH)

option(ENABLE_BUILD_METADATA "Enable build metadata." ON)

set(CMAKE_CXX_STANDARD 20)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_CXX_EXTENSIONS OFF)

set(PROJECT_VERSION_FULL_STRING ${PROJECT_VERSION})
if (DEFINED PROJECT_VERSION_PRERELEASE_IDENTIFIER AND NOT PROJECT_VERSION_PRERELEASE_IDENTIFIER STREQUAL "")
  set(VALID_PRERELEASE_IDENTIFIERS "alpha" "beta" "rc")
  list(FIND VALID_PRERELEASE_IDENTIFIERS "${PROJECT_VERSION_PRERELEASE_IDENTIFIER}" INDEX)
  if(INDEX EQUAL -1)
    message(FATAL_ERROR "Unsupported PROJECT_VERSION_PRERELEASE_IDENTIFIER value: ${PROJECT_VERSION_PRERELEASE_IDENTIFIER}. Valid values are: ${VALID_PRERELEASE_IDENTIFIERS}")
  endif()

  string(APPEND PROJECT_VERSION_FULL_STRING "-${PROJECT_VERSION_PRERELEASE_IDENTIFIER}")
  if (DEFINED PROJECT_VERSION_PRERELEASE_PATCH AND NOT PROJECT_VERSION_PRERELEASE_PATCH STREQUAL "")
    string(APPEND PROJECT_VERSION_FULL_STRING ".${PROJECT_VERSION_PRERELEASE_PATCH}")
  endif()
elseif (DEFINED PROJECT_VERSION_PRERELEASE_PATCH AND NOT PROJECT_VERSION_PRERELEASE_PATCH STREQUAL "")
  message(FATAL_ERROR "PROJECT_VERSION_PRERELEASE_IDENTIFIER must be set in order to use PROJECT_VERSION_PRERELEASE_PATCH.")
endif()

set(PROJECT_BUILD_METADATA_ENABLED false)
if (ENABLE_BUILD_METADATA)
  find_package(Git QUIET)

  if(NOT Git_FOUND)
    message(FATAL_ERROR "Git executable not found. Cannot add build metadata.")
  endif()
  
  execute_process(
    COMMAND ${GIT_EXECUTABLE} rev-parse HEAD
    WORKING_DIRECTORY ${CMAKE_SOURCE_DIR}
    OUTPUT_VARIABLE PROJECT_BUILD_METADATA_REVISION
    OUTPUT_STRIP_TRAILING_WHITESPACE
    ERROR_QUIET
  )

  execute_process(
    COMMAND ${GIT_EXECUTABLE} rev-parse --abbrev-ref HEAD
    WORKING_DIRECTORY ${CMAKE_SOURCE_DIR}
    OUTPUT_VARIABLE PROJECT_BUILD_METADATA_BRANCH
    OUTPUT_STRIP_TRAILING_WHITESPACE
    ERROR_QUIET
  )

  set(PROJECT_BUILD_METADATA_ENABLED true)
endif()

if (NOT IS_DIRECTORY ${CMAKE_INSTALL_PREFIX})
  message(FATAL_ERROR "CMAKE_INSTALL_PREFIX either does not exist or is not a directory.")
elseif(NOT IS_ABSOLUTE ${CMAKE_INSTALL_PREFIX})
  message(FATAL_ERROR "CMAKE_INSTALL_PREFIX is not an absolute path.")
else()
  # Get the mod folder.
  cmake_path(GET CMAKE_INSTALL_PREFIX FILENAME MOD_FOLDER)
  # Get the game directory.
  cmake_path(GET CMAKE_INSTALL_PREFIX PARENT_PATH GAME_DIR)
endif()

# Mod directory is the install directory.
set(MOD_DIR ${CMAKE_INSTALL_PREFIX})

# SDK directories definitions
set(CL_DLL_DIR ${CMAKE_CURRENT_SOURCE_DIR}/cl_dll)
set(COMMON_DIR ${CMAKE_CURRENT_SOURCE_DIR}/common)
set(DLLS_DIR ${CMAKE_CURRENT_SOURCE_DIR}/dlls)
set(ENGINE_DIR ${CMAKE_CURRENT_SOURCE_DIR}/engine)
set(EXTERNAL_DIR ${CMAKE_CURRENT_SOURCE_DIR}/external)
set(GAME_SHARED_DIR ${CMAKE_CURRENT_SOURCE_DIR}/game_shared)
set(LIB_DIR ${CMAKE_CURRENT_SOURCE_DIR}/lib)
set(PM_SHARED_DIR ${CMAKE_CURRENT_SOURCE_DIR}/pm_shared)
set(PUBLIC_DIR ${CMAKE_CURRENT_SOURCE_DIR}/public)
set(UTILS_DIR ${CMAKE_CURRENT_SOURCE_DIR}/utils)
set(MOD_FILES_DIR ${CMAKE_CURRENT_SOURCE_DIR}/mod_files)

# Mod configuration file
set(MOD_CONFIG_FILE_PATH ${COMMON_DIR}/mod_config.h)
configure_file(
  ${CMAKE_CURRENT_SOURCE_DIR}/cmake/mod_config.h.in
  ${MOD_CONFIG_FILE_PATH}
  @ONLY
)

add_subdirectory(cl_dll)
add_subdirectory(dlls)

#====================================
# MOD FILES INSTALLATION
#====================================

# Download and install base mod files.
#include(FetchContent)

#FetchContent_Populate(
#  mod_base_files
#  URL 
#  URL_HASH 
#)

#install(DIRECTORY "${mod_base_files_SOURCE_DIR}/" DESTINATION .)

# Install changelog and licenses.
install(FILES "${CMAKE_CURRENT_SOURCE_DIR}/CHANGELOG.md" DESTINATION .)
install(DIRECTORY "${CMAKE_CURRENT_SOURCE_DIR}/licenses" DESTINATION .)

# Install additional mod files.
install(DIRECTORY mod_files/ DESTINATION .)

#====================================
# MOD PACKAGING
#====================================

set(CPACK_PACKAGE_NAME "release" CACHE STRING "Prefix to prepend to the name of the mod package.")
set(CPACK_GENERATOR "ZIP")
set(CPACK_INCLUDE_TOPLEVEL_DIRECTORY OFF)
# Create a root directory named after the mod folder's name inside the package.
set(CPACK_PACKAGING_INSTALL_PREFIX  "/${MOD_FOLDER}")
set(CPACK_PACKAGE_VERSION "${PROJECT_VERSION_FULL_STRING}")
include(CPack)
