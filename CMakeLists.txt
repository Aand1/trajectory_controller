set ( SOURCES
	"src/trajectory_point_follower.cpp"
	"src/interface.cpp"
    "control-systems/src/andromeda.c"
)

set (HEADERS
	"include/trajectory_point_follower.h"
    "control-systems/src/andromeda.h"
)
include_directories("include")
include_directories("dlib_files")
include_directories("control-systems/src")
#add_definitions(-DENABLE_ASSERTS)
set(CMAKE_C_FLAGS "${CMAKE_C_FLAGS} -std=c99")
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -Drestrict=__restrict__") #use restrict in c++, I wonder if this works

add_library (trajectory_point_controller MODULE ${SOURCES} ${HEADERS} "dlib_files")
target_link_libraries(trajectory_point_controller PRIVATE lmscore lms_sensor_utils street_environment lms_math phoenix_CC2016_service)
