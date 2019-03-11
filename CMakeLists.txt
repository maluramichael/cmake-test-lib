cmake_minimum_required(VERSION 3.13)
project(pancake)

include(GNUInstallDirs)

add_library(
  pancake
  src/core/game.cpp
)

target_include_directories(
  pancake PUBLIC
  $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}/include/>
  $<INSTALL_INTERFACE:${CMAKE_INSTALL_INCLUDEDIR}>
)

install(
  TARGETS pancake
  EXPORT pancake-config
  ARCHIVE DESTINATION ${CMAKE_INSTALL_LIBDIR}
)

install(
  EXPORT pancake-config
  NAMESPACE pancake::
  DESTINATION ${CMAKE_INSTALL_LIBDIR}/cmake/pancake
)

install(
  DIRECTORY ${CMAKE_CURRENT_LIST_DIR}/include/pancake/
  DESTINATION ${CMAKE_INSTALL_INCLUDEDIR}/pancake
)
