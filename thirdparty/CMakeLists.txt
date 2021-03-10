
aux_source_directory(${CMAKE_CURRENT_LIST_DIR}/glad GLAD_SRC)
aux_source_directory(${CMAKE_CURRENT_LIST_DIR}/FastNoise NOISE_SRC)
aux_source_directory(${CMAKE_CURRENT_LIST_DIR}/stb_image STB_IMAGE_SRC)

set(THIRDPARTY_SRC
        ${GLAD_SRC}
        ${NOISE_SRC}
        ${STB_IMAGE_SRC})

find_library(GLFW
        NAMES libglfw3.a
        HINTS ${CMAKE_CURRENT_LIST_DIR}/libs)

find_library(GLEW
        NAMES libGLEW.a
        HINTS ${CMAKE_CURRENT_LIST_DIR}/libs)

set(THIRDPARTY_LIBS
        ${GLEW}
        ${GLFW})