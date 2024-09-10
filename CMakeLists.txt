cmake_minimum_required(VERSION 3.27)
project(SIMDIS-LIB VERSION 1.0 LANGUAGES CXX)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

add_library(simdis INTERFACE)

target_link_directories(simdis
  INTERFACE
  $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}/lib>
  $<INSTALL_INTERFACE:lib/simdis>
)

target_include_directories(simdis
  INTERFACE
  $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}/include>
  $<INSTALL_INTERFACE:include/simdis>
)

target_link_libraries(simdis
  INTERFACE
  $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}/lib/simCore.lib>
  $<INSTALL_INTERFACE:simCore.lib>
  $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}/lib/simData.lib>
  $<INSTALL_INTERFACE:simData.lib>
  $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}/lib/simNotify.lib>
  $<INSTALL_INTERFACE:simNotify.lib>
  $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}/lib/simQt.lib>
  $<INSTALL_INTERFACE:simQt.lib>
  $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}/lib/simUtil.lib>
  $<INSTALL_INTERFACE:simUtil.lib>
  $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}/lib/simVis.lib>
  $<INSTALL_INTERFACE:simVis.lib>
)

include(CMakePackageConfigHelpers)
configure_package_config_file(
  "${CMAKE_CURRENT_SOURCE_DIR}/simdisConfig.cmake.in"
  "${CMAKE_CURRENT_BINARY_DIR}/simdisConfig.cmake"
  INSTALL_DESTINATION share/simdis
)

install(TARGETS simdis
  EXPORT simdisTargets
  ARCHIVE DESTINATION lib
  LIBRARY DESTINATION lib
  RUNTIME DESTINATION bin
)

install(DIRECTORY
  "${CMAKE_CURRENT_SOURCE_DIR}/include/simCore"
  "${CMAKE_CURRENT_SOURCE_DIR}/include/simData"
  "${CMAKE_CURRENT_SOURCE_DIR}/include/simNotify"
  "${CMAKE_CURRENT_SOURCE_DIR}/include/simQt"
  "${CMAKE_CURRENT_SOURCE_DIR}/include/simUtil"
  "${CMAKE_CURRENT_SOURCE_DIR}/include/simVis"
  DESTINATION include/simdis
)

install(FILES
  "${CMAKE_CURRENT_SOURCE_DIR}/lib/simCore.lib"
  "${CMAKE_CURRENT_SOURCE_DIR}/lib/simData.lib"
  "${CMAKE_CURRENT_SOURCE_DIR}/lib/simNotify.lib"
  "${CMAKE_CURRENT_SOURCE_DIR}/lib/simQt.lib"
  "${CMAKE_CURRENT_SOURCE_DIR}/lib/simUtil.lib"
  "${CMAKE_CURRENT_SOURCE_DIR}/lib/simVis.lib"
  DESTINATION lib/simdis
)

install(
  EXPORT simdisTargets
  DESTINATION share/simdis
  NAMESPACE simdis::
)

install(FILES
  "${CMAKE_CURRENT_BINARY_DIR}/simdisConfig.cmake"
  DESTINATION share/simdis
)
