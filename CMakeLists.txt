cmake_minimum_required (VERSION 2.6)
project(Assignment1)

#########################################################
# FIND GLUT
#########################################################
find_package(GLUT REQUIRED)
include_directories(${GLUT_INCLUDE_DIRS})
link_directories(${GLUT_LIBRARY_DIRS})
add_definitions(${GLUT_DEFINITIONS})
if(NOT GLUT_FOUND)
    message(ERROR " GLUT not found!")
endif(NOT GLUT_FOUND)

#########################################################
# FIND OPENGL
#########################################################
find_package(OpenGL REQUIRED)
include_directories(${OpenGL_INCLUDE_DIRS})
link_directories(${OpenGL_LIBRARY_DIRS})
add_definitions(${OpenGL_DEFINITIONS})
if(NOT OPENGL_FOUND)
    message(ERROR " OPENGL not found!")
endif(NOT OPENGL_FOUND)

include_directories("${PROJECT_BINARY_DIR}/src")

add_executable(solar src/Solar.c)
add_executable(robot src/robot.c)

target_link_libraries(solar ${OPENGL_LIBRARIES} ${GLUT_LIBRARY} )
target_link_libraries(robot ${OPENGL_LIBRARIES} ${GLUT_LIBRARY} )

install(TARGETS solar DESTINATION bin)
install(TARGETS robot DESTINATION bin)
