add_subdirectory(systems)

# Collect source files into the "sources" variable and unit test files into the
# "gtest_sources" variable.
# gz_get_libsources_and_unittests(sources gtest_sources)

# Collect source and test files manually

set(sources
  Algorithm.cc
  Convert.cc
  Geometry.cc
  Grid.cc
  MeshTools.cc
  OceanTile.cc
  PhysicalConstants.cc
  Physics.cc
  SubMeshWithTangents.cc
  TriangulatedGrid.cc
  Utilities.cc
  Wavefield.cc
  WavefieldSampler.cc
  WaveParameters.cc
  WaveSimulation.cc
  LinearRandomFFTWaveSimulation.cc
  LinearRandomFFTWaveSimulationRef.cc
  LinearRandomWaveSimulation.cc
  LinearRegularWaveSimulation.cc
  TrochoidIrregularWaveSimulation.cc
  WaveSpectrum.cc
  WaveSpreadingFunction.cc
)

# Create the library target
gz_create_core_library(SOURCES ${sources} CXX_STANDARD ${CMAKE_CXX_STANDARD})

target_link_libraries(${PROJECT_LIBRARY_TARGET_NAME}
  PUBLIC
  gz-math${GZ_MATH_VER}
  gz-msgs${GZ_MSGS_VER}::gz-msgs${GZ_MSGS_VER}
  gz-common${GZ_COMMON_VER}::gz-common${GZ_COMMON_VER}
  gz-common${GZ_COMMON_VER}::graphics
  gz-common${GZ_COMMON_VER}::profiler
  gz-transport${GZ_TRANSPORT_VER}::gz-transport${GZ_TRANSPORT_VER}
  sdformat${SDF_VER}::sdformat${SDF_VER}
  ${FFT_LIBRARIES}
)
if (UNIX AND NOT APPLE)
  target_link_libraries(${PROJECT_LIBRARY_TARGET_NAME}
    PRIVATE stdc++fs)
endif()

target_include_directories(${PROJECT_LIBRARY_TARGET_NAME}
  PUBLIC
  $<BUILD_INTERFACE:${CMAKE_CURRENT_BINARY_DIR}>
  ${EIGEN3_INCLUDE_DIR}
)
