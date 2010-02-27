# CMakeLists.txt for src/test-core


# A test executable
LINK_DIRECTORIES (${GLIB2_LIBRARY_DIRS}
  ${GMODULE_LIBRARY_DIRS}
  ${GOBJECT_LIBRARY_DIRS}
  ${GTHREAD_LIBRARY_DIRS}
  ${GCONF2_LIBRARY_DIRS}
)
ADD_EXECUTABLE (test-main
  test-main.c
)

INCLUDE_DIRECTORIES (${GLIB2_INCLUDE_DIRS})
INCLUDE_DIRECTORIES (${LIBINTL_INCLUDE_PATH})
INCLUDE_DIRECTORIES (${REGEX_INCLUDE_PATH})
INCLUDE_DIRECTORIES (${LIBGUILE_INCLUDE_PATH})
INCLUDE_DIRECTORIES (${CMAKE_BINARY_DIR} ) # for config.h
INCLUDE_DIRECTORIES (${CMAKE_SOURCE_DIR}) # for gnc-ui.h
INCLUDE_DIRECTORIES (${CMAKE_SOURCE_DIR}/libqof/qof) # for qof.h
INCLUDE_DIRECTORIES (${CMAKE_SOURCE_DIR}/gnc-module) # for gnc-glib-utils.h
INCLUDE_DIRECTORIES (${CMAKE_SOURCE_DIR}/core-utils) # for gnc-glib-utils.h
INCLUDE_DIRECTORIES (${CMAKE_SOURCE_DIR}/engine) # for gnc-glib-utils.h
INCLUDE_DIRECTORIES (${CMAKE_SOURCE_DIR}/backend/xml)
INCLUDE_DIRECTORIES (${CMAKE_BINARY_DIR}/engine) # for swig-runtime.h

TARGET_LINK_LIBRARIES (test-main gnc-backend-xml engine gnc-module core-utils qof)
TARGET_LINK_LIBRARIES (test-main ${GCONF2_LIBRARIES})
TARGET_LINK_LIBRARIES (test-main ${GTHREAD_LIBRARIES} ${GOBJECT_LIBRARIES} ${GMODULE_LIBRARIES} ${GLIB2_LIBRARIES})
TARGET_LINK_LIBRARIES (test-main ${LIBGUILE_LIBRARIES})
TARGET_LINK_LIBRARIES (test-main ${LIBXML2_LIBRARIES})
TARGET_LINK_LIBRARIES (test-main ${ZLIB_LIBRARIES})
IF (WIN32)
  TARGET_LINK_LIBRARIES (test-main ${LIBINTL_LIBRARY} ${REGEX_LIBRARY})
ENDIF (WIN32)