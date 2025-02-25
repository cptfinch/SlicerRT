project(vtkSlicer${MODULE_NAME}ModuleLogic)

find_package(vtkIECTransformLogic REQUIRED)

set(KIT ${PROJECT_NAME})

set(${KIT}_EXPORT_DIRECTIVE "VTK_SLICER_${MODULE_NAME_UPPER}_MODULE_LOGIC_EXPORT")

set(${KIT}_INCLUDE_DIRECTORIES
  ${SlicerRtCommon_INCLUDE_DIRS}
  ${vtkIECTransformLogic_INCLUDE_DIRS}
  ${vtkSlicer${MODULE_NAME}ModuleMRML_INCLUDE_DIRS}
  )

set(${KIT}_SRCS
  vtkSlicer${MODULE_NAME}Logic.cxx
  vtkSlicer${MODULE_NAME}Logic.h
  )

set(${KIT}_TARGET_LIBRARIES
  ${ITK_LIBRARIES}
  ${PLASTIMATCH_LIBRARIES}
  vtkIECTransformLogic
  vtkSlicer${MODULE_NAME}ModuleMRML
  vtkSlicerBeamsModuleLogic
  vtkSlicerPlanarImageModuleLogic
  vtkSlicerRoomsEyeViewModuleLogic
  vtkSlicerMarkupsModuleMRML
  vtkSlicerRtCommon
  vtkPlmCommon
  )

#-----------------------------------------------------------------------------
SlicerMacroBuildModuleLogic(
  NAME ${KIT}
  EXPORT_DIRECTIVE ${${KIT}_EXPORT_DIRECTIVE}
  INCLUDE_DIRECTORIES ${${KIT}_INCLUDE_DIRECTORIES}
  SRCS ${${KIT}_SRCS}
  TARGET_LIBRARIES ${${KIT}_TARGET_LIBRARIES}
  )
