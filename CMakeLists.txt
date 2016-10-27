cmake_minimum_required(VERSION 2.6)
project(mtcnn_c)

SET(CMAKE_C_COMPILER g++)
SET(CMAK_CXX_COMPILER g++)
add_compile_options(-std=c++11)
add_compile_options(-m64)

include_directories(
    ${mtcnn_c_SOURCE_DIR}/include/ 
    /usr/local/cuda/include)
link_directories(
    ${mtcnn_c_SOURCE_DIR}/lib/
    /usr/local/cuda/lib64)

add_executable(mtcnn_c main.cpp )
target_link_libraries(mtcnn_c 
    -lcaffe 
    -lboost_system 
    -lboost_filesystem
    -lopencv_core 
    -lopencv_highgui 
    -lopencv_imgproc
    -lglog
    -lgflags
    -lprotobuf
    -lm
    -lhdf5
    -lhdf5_hl
)

#install(TARGETS mtcnn_c RUNTIME DESTINATION bin)
