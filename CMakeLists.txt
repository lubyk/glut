# --------------------------------------------------------------
#  glut
#  
#  provides:
#    glut.so
# --------------------------------------------------------------
set(MODULE_NAME glut)
set(target ${MODULE_NAME})

find_package(GLUT REQUIRED)
include_directories(src)

file(GLOB MODULE_SOURCES ${MODULE}/src/*.cpp ${MODULE}/src/${PLAT}/*.cpp ${MODULE}/src/*.c ${MODULE}/src/${PLAT}/*.c)
add_library(${target} MODULE ${MODULE_SOURCES})
set_target_properties(${target}
  PROPERTIES
  LINK_FLAGS ${PLAT_OBJ_FLAGS}
  PREFIX ""
  SUFFIX ".so"
)  
target_link_libraries(${target} ${GLUT_LIBRARIES})

# --------------------------------------------------------------
#  install                                     
# --------------------------------------------------------------
install(TARGETS ${target}
  DESTINATION lib/lubyk
)
