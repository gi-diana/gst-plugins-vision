set (SOURCES
  gstframelinksrc.c)
    
set (HEADERS
  gstframelinksrc.h)

include_directories (AFTER
  ${IMPERX_FLEX_INCLUDE_DIR})

set (libname libgstimperxflex)

add_library (${libname} MODULE
  ${SOURCES}
  ${HEADERS})

target_link_libraries (${libname}
  ${GLIB2_LIBRARIES}
  ${GOBJECT_LIBRARIES}
  ${GSTREAMER_LIBRARY}
  ${GSTREAMER_BASE_LIBRARY}
  ${GSTREAMER_VIDEO_LIBRARY}
  ${IMPERX_FLEX_LIBRARIES})

set (pdbfile "${CMAKE_CURRENT_BINARY_DIR}/\${CMAKE_INSTALL_CONFIG_NAME}/${libname}.pdb")
install (FILES ${pdbfile} DESTINATION lib/gstreamer-1.0 COMPONENT pdb)
install(TARGETS ${libname}
  LIBRARY DESTINATION lib/gstreamer-1.0)
