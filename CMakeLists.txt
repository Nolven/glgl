cmake_minimum_required(VERSION 3.15)
project(glgl)

set(CMAKE_CXX_STANDARD 20)

include_directories(include)
include_directories(include/thirdparty)

aux_source_directory(${PROJECT_SOURCE_DIR}/src SRC)

# Thirdparty
set(THIRDPARTY_PATH ${CMAKE_CURRENT_LIST_DIR}/thirdparty)
include_directories(${THIRDPARTY_PATH})
include(${THIRDPARTY_PATH}/CMakeLists.txt)

add_executable(${PROJECT_NAME} main.cpp ${SRC} ${THIRDPARTY_SRC})
target_link_libraries(${PROJECT_NAME} ${THIRDPARTY_LIBS} -ldl -pthread -lassimp)