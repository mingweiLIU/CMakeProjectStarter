file(GLOB SOURCES "*.hpp" "*.cpp" "*.ui" "*.qrc" "*.h")

add_executable(main ${SOURCES})
# target_link_libraries(CreateProject H2O::h2o_base H2O::osketchpro_frame SketchUpAPI Qt5::Core)

# install(FILES $<TARGET_FILE:CreateProject> DESTINATION ruby/h2o_osketchpro/dlls)