find_package(OpenGL)

if(WIN32)
    set(OPENGL_LIBRARY ${OPENGL_gl_LIBRARY})
else()
    set(OPENGL_LIBRARY OpenGL::OpenGL)
endif()

if(NOT ANDROID)
    find_package(Threads)
endif()

if (UNIX)
    find_library(DL_LIBRARY dl)
endif()

set(SOURCES osggroups.cpp)

add_executable(osggroups ${SOURCES})
target_include_directories(osggroups PRIVATE ${OSG_INCLUDE_DIR})
target_link_libraries(osggroups ${OSGDB_LIBRARIES} ${OSG_LIBRARIES} ${OPENTHREADS_LIBRARY} ${CMAKE_THREAD_LIBS_INIT} ${OPENGL_LIBRARY} ${DL_LIBRARY})

