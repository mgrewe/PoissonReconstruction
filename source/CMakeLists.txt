configure_file(
  ${PoissonReconstruction_SOURCE_DIR}/source/vtkPoissonReconstructionConfigure.h.in
  ${PoissonReconstruction_BINARY_DIR}/vtkPoissonReconstructionConfigure.h
  @ONLY IMMEDIATE
)

add_library( vtkPoissonReconstruction
  ${SHARED_LIBS}
  vtkPoissonReconstruction.cxx
  Factor.cpp
  Geometry.cpp
  MarchingCubes.cpp
  MultiGridOctest.cpp
  MultiGridOctreeData.cpp
)

target_link_libraries( vtkPoissonReconstruction
  ${VTK_LIBRARIES}
)

INSTALL(TARGETS vtkPoissonReconstruction LIBRARY DESTINATION ${LIBRARY_INSTALL_DIR})

FILE(GLOB HEADER_FILES *.h)

SET(HEADER_FILES ${HEADER_FILES} ${PoissonReconstruction_BINARY_DIR}/vtkPoissonReconstructionConfigure.h)

INSTALL(FILES ${HEADER_FILES} DESTINATION ${INCLUDE_INSTALL_DIR}/vtkPoissonReconstruction)

