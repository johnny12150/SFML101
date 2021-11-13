cmake_minimum_required(VERSION 3.20)
project(sfml_games)

set(CMAKE_CXX_STANDARD 14)

add_executable(sfml_games main.cpp)

include_directories(C:/Users/wade/Downloads/SFML/include)

set(SFML_ROOT C:/Users/wade/Downloads/SFML)
set(CMAKE_MODULE_PATH "${CMAKE_CURRENT_LIST_DIR}/cmake_modules")
find_package(SFML REQUIRED system window graphics)
if (SFML_FOUND)
    include_directories(${SFML_INCLUDE_DIR})
    target_link_libraries(sfml_games ${SFML_LIBRARIES})
endif()

# 如果有放圖片/ 聲音才要
#file(COPY assets DESTINATION ${CMAKE_BINARY_DIR})

# Copy dlls to build
if(WIN32)
    file(GLOB BINARY_DEP_DLLS "${SFML_INCLUDE_DIR}/../bin/*.dll")
    file(COPY ${BINARY_DEP_DLLS} DESTINATION ${CMAKE_BINARY_DIR})
    file(GLOB MINGW_DEP_DLLS "C:/Users/wade/Downloads/mingw64/bin/*.dll")
    file(COPY ${MINGW_DEP_DLLS} DESTINATION ${CMAKE_BINARY_DIR})
endif()
