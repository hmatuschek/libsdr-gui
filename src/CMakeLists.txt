set(libsdr_gui_SOURCES spectrum.cc spectrumview.cc waterfallview.cc)
set(libsdr_gui_MOC_HEADERS spectrum.hh spectrumview.hh waterfallview.hh)
set(libsdr_gui_HEADERS ${libsdr_gui_MOC_HEADERS} gui.hh)
qt5_wrap_cpp(libsdr_gui_MOC_SOURCES ${libsdr_gui_MOC_HEADERS})

add_library(libsdr-gui SHARED ${libsdr_gui_SOURCES} ${libsdr_gui_MOC_SOURCES})
set_target_properties(libsdr-gui PROPERTIES OUTPUT_NAME sdr-gui)
set_target_properties(libsdr-gui PROPERTIES VERSION
  "${libsdr_VERSION_MAJOR}.${libsdr_VERSION_MINOR}.${libsdr_VERSION_PATCH}")
set_target_properties(libsdr-gui PROPERTIES SOVERION "${libsdr_VERSION_MAJOR}")
set_target_properties(libsdr-gui PROPERTIES INSTALL_NAME_DIR ${CMAKE_INSTALL_FULL_LIBDIR})
set_target_properties(libsdr-gui PROPERTIES MACOSX_RPATH "${CMAKE_INSTALL_RPATH}")
target_link_libraries(libsdr-gui ${LIBS})

install(TARGETS libsdr-gui DESTINATION ${CMAKE_INSTALL_LIBDIR})
install(FILES ${libsdr_gui_HEADERS} DESTINATION "${CMAKE_INSTALL_INCLUDEDIR}/libsdr/gui")

