cmake_minimum_required(VERSION 3.5)

project(example_recognition LANGUAGES CXX)

find_package(OpenCV REQUIRED)

set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

add_library(miniai_rec SHARED IMPORTED)
set_target_properties(miniai_rec PROPERTIES IMPORTED_LOCATION ${CMAKE_SOURCE_DIR}/../bin/linux_x86_64/libminiai_rec.so)

add_executable(example_recognition main.cpp
    )

target_include_directories(example_recognition
    PUBLIC ${PROJECT_SOURCE_DIR}
    PUBLIC ${OpenCV_INCLUDE_DIRS}
)


target_link_libraries(example_recognition
    miniai_rec
    ${OpenCV_LIBS}
)
