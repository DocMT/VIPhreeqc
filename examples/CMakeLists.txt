if (WIN32)
SET(EXAMPLES_DIR examples)
else()
SET(EXAMPLES_DIR ${CMAKE_INSTALL_DOCDIR}/examples)
endif()
if(NOT EMSCRIPTEN)
  add_subdirectory(c)
  add_subdirectory(com)
  add_subdirectory(cpp)
  add_subdirectory(fortran)
  add_subdirectory(using-cmake)
else()
  add_subdirectory(html)
endif()