cmake_minimum_required(VERSION 3.15)
project(untitled)

set(CMAKE_CXX_STANDARD 17)

include_directories(include)

include_directories(include/thirdparty)
link_directories(include/thirdparty)

aux_source_directory(${PROJECT_SOURCE_DIR}/src SRC)
aux_source_directory(${PROJECT_SOURCE_DIR}/src/thirdparty THIRDPARTY)

set(THIRDPARTY_PATH ${CMAKE_CURRENT_LIST_DIR}/thirdparty)
include_directories(${THIRDPARTY_PATH})

aux_source_directory(${THIRDPARTY_PATH} THIRDPARTY_SRC)
aux_source_directory(${THIRDPARTY_PATH}/glad GLAD_SRC)
aux_source_directory(${THIRDPARTY_PATH}/FastNoise NOISE_SRC)
aux_source_directory(${THIRDPARTY_PATH}/stb_image STB_IMAGE_SRC)

find_library(GLFW
        NAMES libglfw3.a
        HINTS ${THIRDPARTY_PATH}/libs)

find_library(GLEW
        NAMES libGLEW.a
        HINTS ${THIRDPARTY_PATH}/libs)

add_executable(${PROJECT_NAME} main.cpp ${SRC} ${THIRDPARTY} ${THIRDPARTY_SRC} ${GLAD_SRC} ${NOISE_SRC} ${STB_IMAGE_SRC})
target_link_libraries(${PROJECT_NAME} ${GLEW} ${GLFW} -ldl -lgtest -pthread -lassimp)