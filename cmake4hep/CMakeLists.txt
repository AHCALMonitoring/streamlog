########################################################
# cmake file for installing cmake4hep
# @author Jan Engels, Desy IT
CMAKE_MINIMUM_REQUIRED( VERSION 2.6 )
########################################################


PROJECT( cmake4hep )


# --------- version ----------------
SET( ${PROJECT_NAME}_VERSION_MAJOR 0 )
SET( ${PROJECT_NAME}_VERSION_MINOR 1 )
SET( ${PROJECT_NAME}_VERSION_PATCH 0 )
SET( ${PROJECT_NAME}_VERSION ${${PROJECT_NAME}_VERSION_MAJOR}.${${PROJECT_NAME}_VERSION_MINOR}.${${PROJECT_NAME}_VERSION_PATCH} )
# -----------------------------------------------


INCLUDE( set_default_install_prefix.cmake )
INCLUDE( set_default_uninstall_target.cmake )
INCLUDE( MacroGeneratePackageConfigFiles.cmake )

IF( NOT "${CMAKE_INSTALL_PREFIX}" STREQUAL "${PROJECT_SOURCE_DIR}" )
    INSTALL( DIRECTORY . DESTINATION ${CMAKE_INSTALL_PREFIX}/${PROJECT_NAME}
        PATTERN ".svn" EXCLUDE
        PATTERN "CMakeLists.txt" EXCLUDE # this file
        PATTERN "cmake" EXCLUDE # directory containing configuration files
    )
    INSTALL( FILES doc/index.html DESTINATION ${CMAKE_INSTALL_PREFIX}/doc/cmake4hep )
ENDIF()

# generate and install cmake configuration files
GENERATE_PACKAGE_CONFIGURATION_FILES( ${PROJECT_NAME}Config.cmake ${PROJECT_NAME}ConfigVersion.cmake )

