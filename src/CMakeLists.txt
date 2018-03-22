# Build library
add_library(MagnumImGui MagnumImGui.cpp ${MagnumImGuiShaders_RCS})

install(TARGETS MagnumImGui DESTINATION "lib/")
install(FILES MagnumImGui.h DESTINATION "include/MagnumImGui")

# Build exmaple
add_executable(Example Example.cpp)


find_library(IMGUI_LIB ImGui)
target_link_libraries(Example
  Magnum::Application
  Magnum::Magnum
  Magnum::Shaders
  MagnumImGui
  ${IMGUI_LIB})
