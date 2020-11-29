cmake_minimum_required(VERSION 3.13)
project(ngl)

set(CMAKE_CXX_STANDARD 17)

set(NGL_ROOT ${CMAKE_SOURCE_DIR})

add_custom_target(ngl_doc ALL
        COMMAND ${MKDOCS_ROOT} build
        COMMENT "Build doc - Output : ${NGL_DOC_OUTPUT}"
        WORKING_DIRECTORY ${NGL_ROOT}/doc
        )

if (NGL_MODULE_COMPILER)
    add_subdirectory(ngl.compiler)
endif()