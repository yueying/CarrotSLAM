ADD_EXECUTABLE(carrotslam_orbslam main.cpp)

if(MSVC)
SET(LINKLIBS carrotslam_core
carrotslam_nodes
carrotslam_types
pugixml
glog)
else(MSVC)
SET(LINKLIBS libcarrotslam_core.a
libcarrotslam_nodes.a
libcarrotslam_types.a
libpugixml.a
libglog.so
libgflags.so)
endif(MSVC)

TARGET_LINK_LIBRARIES(carrotslam_orbslam
${LINKLIBS}
${OpenCV_LIBS}
${Boost_LIBRARIES}
)
