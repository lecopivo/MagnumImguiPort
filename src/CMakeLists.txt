# Build library

file(GLOB ImGui_SRC "../imgui/*.cpp")

add_library(MagnumImGui MagnumImGui.cpp ${ImGui_SRC} ${MagnumImGuiShaders_RCS})

file(GLOB include_files . "*.h" "../imgui/*.h")
install(TARGETS MagnumImGui DESTINATION "lib/")
install(FILES ${include_files} DESTINATION "include/MagnumImGui")

# Build exmaple

add_executable(Example Example.cpp)

target_link_libraries(Example
  Magnum::Application
  Magnum::Magnum
  Magnum::Shaders
  MagnumImGui)

if(CORRADE_TARGET_EMSCRIPTEN)
    install(TARGETS Example DESTINATION ${CMAKE_INSTALL_PREFIX})
    install(FILES
        Example.html
        EmscriptenApplication.js
        WebApplication.css
        DESTINATION ${CMAKE_INSTALL_PREFIX})
    install(FILES
        ${CMAKE_CURRENT_BINARY_DIR}/Exmaple.js.mem
        ${CMAKE_CURRENT_BINARY_DIR}/Example.wasm
        DESTINATION ${CMAKE_INSTALL_PREFIX} OPTIONAL)
endif()
