cmake_minimum_required(VERSION 3.20)
project(imgui VERSION 1.0)

add_library(imgui STATIC imconfig.h imgui.h imgui.cpp imgui_demo.cpp
  imgui_draw.cpp imgui_internal.h imgui_tables.cpp imgui_widgets.cpp
  imstb_rectpack.h imstb_textedit.h imstb_truetype.h)
  
if(IMGUI_GLFW)
  target_sources(imgui PRIVATE backends/imgui_impl_glfw.cpp
    backends/imgui_impl_glfw.h)
endif()

if(IMGUI_OPENGL3)
  target_sources(imgui PRIVATE backends/imgui_impl_opengl3.cpp
    backends/imgui_impl_opengl3.h backends/imgui_impl_opengl3_loader.h)
endif()
  
install(TARGETS imgui
        EXPORT imguiTargets
        RUNTIME DESTINATION "${CMAKE_INSTALL_BINDIR}"
        ARCHIVE DESTINATION "${CMAKE_INSTALL_LIBDIR}"
        LIBRARY DESTINATION "${CMAKE_INSTALL_LIBDIR}")
