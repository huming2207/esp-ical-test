set(COMPONENT_SRCS "hello_world_main.c")
set(COMPONENT_ADD_INCLUDEDIRS "")

register_component()

option(STATIC_ONLY true)
option(SHARED_ONLY false)

add_subdirectory(../lib/ical)

# Propagate compile settings to libical
target_include_directories(libical PRIVATE ${IDF_INCLUDE_DIRECTORIES})
target_compile_options(libical PRIVATE "${IDF_COMPILE_OPTIONS}")
target_compile_options(libical PRIVATE "${IDF_CXX_COMPILE_OPTIONS}")

target_link_libraries(${COMPONENT_TARGET} libical)
