include_directories(
  ${PROJECT_BINARY_DIR}/include
  ${PROJECT_SOURCE_DIR}
  ${PROJECT_SOURCE_DIR}/pompeii
  ${CMAKE_CURRENT_BINARY_DIR}
)

source_group(\\ FILES CMakeLists.txt)

set( GLFWPOMPEII_PUBLIC_HEADERS
  GLFWVulkanWindow.h
)
set( GLFWPOMPEII_SOURCES
  GLFWVulkanWindow.cpp
)

set( GLFWPOMPEII_LINK_LIBRARIES
  ${GLFW3_LIBRARIES}
  pompeii
)

set( GLFWPOMPEII_INCLUDE_NAME glfwPompeii )
set( GLFWPOMPEII_NAMESPACE glfwPompeii )

common_library( glfwPompeii )

target_include_directories( glfwPompeii
  PUBLIC    "${CMAKE_SOURCE_DIR}"
)



configure_file(
  ${CMAKE_CURRENT_SOURCE_DIR}/routes.h.in
  ${CMAKE_CURRENT_BINARY_DIR}/routes.h)

set( GLFWRENDER_SOURCES
  demo.cpp
)
set( GLFWRENDER_LINK_LIBRARIES
  pompeii
  glfwPompeii
)
common_application( GLFWRender )

set( GLFWTRIANGLE_SOURCES
  triangle.cpp
)
set( GLFWTRIANGLE_LINK_LIBRARIES
  pompeii
  glfwPompeii
)
common_application( GLFWTriangle )