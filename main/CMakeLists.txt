set(COMPONENT_SRCS "hello_world_main.c")
set(COMPONENT_ADD_INCLUDEDIRS "")

register_component()

set(STATIC_ONLY ON CACHE BOOL "Build libical static library" FORCE)
set(ENABLE_GTK_DOC CACHE BOOL "Disable GTK doc for libical" FORCE)

add_subdirectory(lib/ical)

# Propagate compile settings to libical
target_include_directories(ical PRIVATE ${IDF_INCLUDE_DIRECTORIES})
target_compile_options(ical PRIVATE "${IDF_COMPILE_OPTIONS}")
target_compile_options(ical PRIVATE "${IDF_CXX_COMPILE_OPTIONS}")

target_link_libraries(${COMPONENT_TARGET} ical)
