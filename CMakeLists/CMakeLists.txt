#*******简单版本的CMakeLists*******
# 最小版本要求
cmake_minimum_required(VERSION 3.4.1)

# 项目名称 区分大小写
project(PRINT)

set(OUTPUT_NAME "exe.out")

# 设置编译器
set(CMAKE_CXX_COMPILER "g++")

# 设置编译选项
add_definitions(-std=c++11)

# 获得所有source文件
aux_source_directory(${PROJECT_SOURCE_DIR}/src SRC_LIST)

# 添加头文件所在的文件夹
include_directories(${PROJECT_SOURCE_DIR}/include)

# 寻找package
find_package(OpenCV REQUIRED)
# include_directories(${OpenCV_INCLUDE_DIRS})

# 打印消息，测试内部变量
message(STATUS "This pro name is: " ${PROJECT_NAME})
message(STATUS "This is src dir: " ${PROJECT_SOURCE_DIR})
message(STATUS "This is bin dir: " ${PROJECT_BINARY_DIR})
message(STATUS "This is c++ compliter: " ${CMAKE_CXX_COMPILER})
message(STATUS "All source list: " ${SRC_LST})
message(STATUS "All complier flags: " ${CMAKE_CXX_STANDARD})
message(STATUS "OpenCV include dirs: " ${OpenCV_INCLUDE_DIRS})
message(STATUS "OpenCV libs: " ${OpenCV_LIBS})


add_executable(${OUTPUT_NAME} ${SRC_LIST})
target_link_libraries(${OUTPUT_NAME} ${OpenCV_LIBS})

#*******多工程目录版本的CMakeLists*******
# 最小版本要求
cmake_minimum_required(VERSION 3.4.1)

# 项目名称 区分大小写
project(Dynamic_trajectory_planning)

set(OUTPUT_NAME "exe.out")

# 设置编译器
set(CMAKE_CXX_COMPILER "g++")

# 设置编译选项
add_definitions(-std=c++11)

# 寻找package
find_package(OpenCV REQUIRED)

# 添加头文件所在的文件夹
include_directories(${PROJECT_SOURCE_DIR}/include)

add_subdirectory(${PROJECT_SOURCE_DIR}/include)

# 获得所有source文件
set(SRC_LIST main.cpp)

# 相当于g++ -L命令，目的告诉g++编译器，这个path中有需要的库
link_directories(${PROJECT_SOURCE_DIR}/lib)

add_executable(${OUTPUT_NAME} ${SRC_LIST})
target_link_libraries(${OUTPUT_NAME} ${OpenCV_LIBS} self)

#***子目录***
# 多目录工程，一般将每一个子目录编译为静态或者动态链接库，以供主目录调用
aux_source_directory(${PROJECT_SOURCE_DIR}/include CUR_LIST)

# 相当于g++ -I命令，目的让g++编译的时候找到头文件
include_directories(${PROJECT_SOURCE_DIR}/include)  

add_library(self ${CUR_LIST})

target_link_libraries(self ${OpenCV_LIBS})

set(LIBRARY_OUTPUT_PATH ${PROJECT_SOURCE_DIR}/lib)
