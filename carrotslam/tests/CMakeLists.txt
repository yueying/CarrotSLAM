INCLUDE_DIRECTORIES("${CMAKE_CURRENT_SOURCE_DIR}/include")
#ADD_LIBRARY(carrotslam_tests
#  tum_dataset_reader_test.cpp
#)

if(MSVC)
SET(LINKLIBS carrotslam_core
carrotslam_nodes
pugixml
glog)
else(MSVC)
SET(LINKLIBS libcarrotslam_core.a
libcarrotslam_nodes.a
#libcarrotslam_core${CMAKE_DEBUG_POSTFIX}.a
#libcarrotslam_nodes${CMAKE_DEBUG_POSTFIX}.a
libpugixml.a
libglog.so
libgflags.so)
endif(MSVC)

ADD_EXECUTABLE(carrotslam_tests tum_dataset_reader_test.cpp)
TARGET_LINK_LIBRARIES(carrotslam_tests

${LINKLIBS}
${OpenCV_LIBS}
${Boost_LIBRARIES}
)

# 设置将项目添加到包中
if(ENABLE_SOLUTION_FOLDERS)
	set_target_properties(carrotslam_tests PROPERTIES FOLDER "app")
else(ENABLE_SOLUTION_FOLDERS)
	SET_TARGET_PROPERTIES(carrotslam_tests  PROPERTIES PROJECT_LABEL "(app) carrotslam_tests")
endif(ENABLE_SOLUTION_FOLDERS)