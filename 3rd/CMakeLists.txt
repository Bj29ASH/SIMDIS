cmake_minimum_required(VERSION 3.27)
project(SIMDIS-3rd-party-LIB VERSION 1.0 LANGUAGES CXX)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

add_library(simdis_3rd_party INTERFACE)

target_link_directories(simdis_3rd_party
  INTERFACE
  $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}/win64_vc-14.3/OpenSceneGraph/3.6.5/lib>
  $<INSTALL_INTERFACE:lib/simdis_3rd_party/OpenSceneGraph>
  $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}/win64_vc-14.3/osgEarth/OSG-3.6.5/lib>
  $<INSTALL_INTERFACE:lib/simdis_3rd_party/osgEarth>
)

target_include_directories(simdis_3rd_party
  INTERFACE
  $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}/win64_vc-14.3/OpenSceneGraph/3.6.5/include>
  $<INSTALL_INTERFACE:include/simdis_3rd_party/OpenSceneGraph>
  $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}/win64_vc-14.3/osgEarth/OSG-3.6.5/include>
  $<INSTALL_INTERFACE:include/simdis_3rd_party/osgEarth>
)

target_link_libraries(simdis_3rd_party
  INTERFACE
  $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}/win64_vc-14.3/OpenSceneGraph/3.6.5/lib/OpenThreads.lib>
  $<INSTALL_INTERFACE:OpenThreads.lib>
  $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}/win64_vc-14.3/OpenSceneGraph/3.6.5/lib/osg.lib>
  $<INSTALL_INTERFACE:osg.lib>
  $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}/win64_vc-14.3/OpenSceneGraph/3.6.5/lib/osgAnimation.lib>
  $<INSTALL_INTERFACE:osgAnimation.lib>
  $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}/win64_vc-14.3/OpenSceneGraph/3.6.5/lib/osgDB.lib>
  $<INSTALL_INTERFACE:osgDB.lib>
  $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}/win64_vc-14.3/OpenSceneGraph/3.6.5/lib/osgFX.lib>
  $<INSTALL_INTERFACE:osgFX.lib>
  $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}/win64_vc-14.3/OpenSceneGraph/3.6.5/lib/osgGA.lib>
  $<INSTALL_INTERFACE:osgGA.lib>
  $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}/win64_vc-14.3/OpenSceneGraph/3.6.5/lib/osgManipulator.lib>
  $<INSTALL_INTERFACE:osgManipulator.lib>
  $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}/win64_vc-14.3/OpenSceneGraph/3.6.5/lib/osgParticle.lib>
  $<INSTALL_INTERFACE:osgParticle.lib>
  $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}/win64_vc-14.3/OpenSceneGraph/3.6.5/lib/osgPresentation.lib>
  $<INSTALL_INTERFACE:osgPresentation.lib>
  $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}/win64_vc-14.3/OpenSceneGraph/3.6.5/lib/osgShadow.lib>
  $<INSTALL_INTERFACE:osgShadow.lib>
  $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}/win64_vc-14.3/OpenSceneGraph/3.6.5/lib/osgSim.lib>
  $<INSTALL_INTERFACE:osgSim.lib>
  $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}/win64_vc-14.3/OpenSceneGraph/3.6.5/lib/osgTerrain.lib>
  $<INSTALL_INTERFACE:osgTerrain.lib>
  $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}/win64_vc-14.3/OpenSceneGraph/3.6.5/lib/osgText.lib>
  $<INSTALL_INTERFACE:osgText.lib>
  $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}/win64_vc-14.3/OpenSceneGraph/3.6.5/lib/osgUI.lib>
  $<INSTALL_INTERFACE:osgUI.lib>
  $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}/win64_vc-14.3/OpenSceneGraph/3.6.5/lib/osgViewer.lib>
  $<INSTALL_INTERFACE:osgViewer.lib>
  $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}/win64_vc-14.3/OpenSceneGraph/3.6.5/lib/osgVolume.lib>
  $<INSTALL_INTERFACE:osgVolume.lib>
  $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}/win64_vc-14.3/OpenSceneGraph/3.6.5/lib/osgWidget.lib>
  $<INSTALL_INTERFACE:osgWidget.lib>
  $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}/win64_vc-14.3/osgEarth/OSG-3.6.5/lib/osgEarth.lib>
  $<INSTALL_INTERFACE:osgEarth.lib>
  $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}/win64_vc-14.3/osgEarth/OSG-3.6.5/lib/osgEarthSilverLining.lib>
  $<INSTALL_INTERFACE:osgEarthSilverLining.lib>
  $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}/win64_vc-14.3/osgEarth/OSG-3.6.5/lib/osgEarthTriton.lib>
  $<INSTALL_INTERFACE:osgEarthTriton.lib>
)

include(CMakePackageConfigHelpers)
configure_package_config_file(
  "${CMAKE_CURRENT_SOURCE_DIR}/simdis_3rd_partyConfig.cmake.in"
  "${CMAKE_CURRENT_BINARY_DIR}/simdis_3rd_partyConfig.cmake"
  INSTALL_DESTINATION share/simdis_3rd_party
)

install(TARGETS simdis_3rd_party
  EXPORT simdis_3rd_partyTargets
  ARCHIVE DESTINATION lib
  LIBRARY DESTINATION lib
  RUNTIME DESTINATION bin
)

install(DIRECTORY
  "${CMAKE_CURRENT_SOURCE_DIR}/win64_vc-14.3/OpenSceneGraph/3.6.5/include/GL"
  "${CMAKE_CURRENT_SOURCE_DIR}/win64_vc-14.3/OpenSceneGraph/3.6.5/include/OpenThreads"
  "${CMAKE_CURRENT_SOURCE_DIR}/win64_vc-14.3/OpenSceneGraph/3.6.5/include/osg"
  "${CMAKE_CURRENT_SOURCE_DIR}/win64_vc-14.3/OpenSceneGraph/3.6.5/include/osgAnimation"
  "${CMAKE_CURRENT_SOURCE_DIR}/win64_vc-14.3/OpenSceneGraph/3.6.5/include/osgDB"
  "${CMAKE_CURRENT_SOURCE_DIR}/win64_vc-14.3/OpenSceneGraph/3.6.5/include/osgFX"
  "${CMAKE_CURRENT_SOURCE_DIR}/win64_vc-14.3/OpenSceneGraph/3.6.5/include/osgGA"
  "${CMAKE_CURRENT_SOURCE_DIR}/win64_vc-14.3/OpenSceneGraph/3.6.5/include/osgManipulator"
  "${CMAKE_CURRENT_SOURCE_DIR}/win64_vc-14.3/OpenSceneGraph/3.6.5/include/osgParticle"
  "${CMAKE_CURRENT_SOURCE_DIR}/win64_vc-14.3/OpenSceneGraph/3.6.5/include/osgPresentation"
  "${CMAKE_CURRENT_SOURCE_DIR}/win64_vc-14.3/OpenSceneGraph/3.6.5/include/osgShadow"
  "${CMAKE_CURRENT_SOURCE_DIR}/win64_vc-14.3/OpenSceneGraph/3.6.5/include/osgSim"
  "${CMAKE_CURRENT_SOURCE_DIR}/win64_vc-14.3/OpenSceneGraph/3.6.5/include/osgTerrain"
  "${CMAKE_CURRENT_SOURCE_DIR}/win64_vc-14.3/OpenSceneGraph/3.6.5/include/osgText"
  "${CMAKE_CURRENT_SOURCE_DIR}/win64_vc-14.3/OpenSceneGraph/3.6.5/include/osgUI"
  "${CMAKE_CURRENT_SOURCE_DIR}/win64_vc-14.3/OpenSceneGraph/3.6.5/include/osgUtil"
  "${CMAKE_CURRENT_SOURCE_DIR}/win64_vc-14.3/OpenSceneGraph/3.6.5/include/osgViewer"
  "${CMAKE_CURRENT_SOURCE_DIR}/win64_vc-14.3/OpenSceneGraph/3.6.5/include/osgVolume"
  "${CMAKE_CURRENT_SOURCE_DIR}/win64_vc-14.3/OpenSceneGraph/3.6.5/include/osgWidget"
  DESTINATION include/simdis_3rd_party/OpenSceneGraph
)

install(DIRECTORY
  "${CMAKE_CURRENT_SOURCE_DIR}/win64_vc-14.3/osgEarth/OSG-3.6.5/include/osgEarth"
  "${CMAKE_CURRENT_SOURCE_DIR}/win64_vc-14.3/osgEarth/OSG-3.6.5/include/osgEarthDrivers"
  "${CMAKE_CURRENT_SOURCE_DIR}/win64_vc-14.3/osgEarth/OSG-3.6.5/include/osgEarthSilverLining"
  "${CMAKE_CURRENT_SOURCE_DIR}/win64_vc-14.3/osgEarth/OSG-3.6.5/include/osgEarthTriton"
  DESTINATION include/simdis_3rd_party/osgEarth
)

install(FILES
  "${CMAKE_CURRENT_SOURCE_DIR}/win64_vc-14.3/OpenSceneGraph/3.6.5/lib/OpenThreads.lib"
  "${CMAKE_CURRENT_SOURCE_DIR}/win64_vc-14.3/OpenSceneGraph/3.6.5/lib/osg.lib"
  "${CMAKE_CURRENT_SOURCE_DIR}/win64_vc-14.3/OpenSceneGraph/3.6.5/lib/osgAnimation.lib"
  "${CMAKE_CURRENT_SOURCE_DIR}/win64_vc-14.3/OpenSceneGraph/3.6.5/lib/osgDB.lib"
  "${CMAKE_CURRENT_SOURCE_DIR}/win64_vc-14.3/OpenSceneGraph/3.6.5/lib/osgFX.lib"
  "${CMAKE_CURRENT_SOURCE_DIR}/win64_vc-14.3/OpenSceneGraph/3.6.5/lib/osgGA.lib"
  "${CMAKE_CURRENT_SOURCE_DIR}/win64_vc-14.3/OpenSceneGraph/3.6.5/lib/osgManipulator.lib"
  "${CMAKE_CURRENT_SOURCE_DIR}/win64_vc-14.3/OpenSceneGraph/3.6.5/lib/osgParticle.lib"
  "${CMAKE_CURRENT_SOURCE_DIR}/win64_vc-14.3/OpenSceneGraph/3.6.5/lib/osgPresentation.lib"
  "${CMAKE_CURRENT_SOURCE_DIR}/win64_vc-14.3/OpenSceneGraph/3.6.5/lib/osgShadow.lib"
  "${CMAKE_CURRENT_SOURCE_DIR}/win64_vc-14.3/OpenSceneGraph/3.6.5/lib/osgSim.lib"
  "${CMAKE_CURRENT_SOURCE_DIR}/win64_vc-14.3/OpenSceneGraph/3.6.5/lib/osgTerrain.lib"
  "${CMAKE_CURRENT_SOURCE_DIR}/win64_vc-14.3/OpenSceneGraph/3.6.5/lib/osgText.lib"
  "${CMAKE_CURRENT_SOURCE_DIR}/win64_vc-14.3/OpenSceneGraph/3.6.5/lib/osgUI.lib"
  "${CMAKE_CURRENT_SOURCE_DIR}/win64_vc-14.3/OpenSceneGraph/3.6.5/lib/osgUtil.lib"
  "${CMAKE_CURRENT_SOURCE_DIR}/win64_vc-14.3/OpenSceneGraph/3.6.5/lib/osgViewer.lib"
  "${CMAKE_CURRENT_SOURCE_DIR}/win64_vc-14.3/OpenSceneGraph/3.6.5/lib/osgVolume.lib"
  "${CMAKE_CURRENT_SOURCE_DIR}/win64_vc-14.3/OpenSceneGraph/3.6.5/lib/osgWidget.lib"
  DESTINATION lib/simdis_3rd_party/OpenSceneGraph
)

install(FILES
  "${CMAKE_CURRENT_SOURCE_DIR}/win64_vc-14.3/osgEarth/OSG-3.6.5/lib/osgEarth.lib"
  "${CMAKE_CURRENT_SOURCE_DIR}/win64_vc-14.3/osgEarth/OSG-3.6.5/lib/osgEarthSilverLining.lib"
  "${CMAKE_CURRENT_SOURCE_DIR}/win64_vc-14.3/osgEarth/OSG-3.6.5/lib/osgEarthTriton.lib"
  DESTINATION lib/simdis_3rd_party/osgEarth
)

install(DIRECTORY
  "${CMAKE_CURRENT_SOURCE_DIR}/win64_vc-14.3/OpenSceneGraph/3.6.5/bin"
  DESTINATION /
)

install(DIRECTORY
  "${CMAKE_CURRENT_SOURCE_DIR}/win64_vc-14.3/osgEarth/OSG-3.6.5/bin"
  DESTINATION /
)

install(
  EXPORT simdis_3rd_partyTargets
  DESTINATION share/simdis_3rd_party
  NAMESPACE simdis_3rd_party::
)

install(
  FILES
  "${CMAKE_CURRENT_BINARY_DIR}/simdis_3rd_partyConfig.cmake"
  DESTINATION share/simdis_3rd_party
)
