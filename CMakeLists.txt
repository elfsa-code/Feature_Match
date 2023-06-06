# CMake 最低版本号要求2.8
cmake_minimum_required(VERSION 2.8)

# 项目名称feature_match
project(feature_match)

# 设置编译方式Release
set(CMAKE_BUILD_TYPE "Debug" )

# 支持C++11 -o3优化
set(CMAKE_CXX_FLAGS "-std=c++11 -O3" )

# 查找系统里的OpenCV，找不到输出警告信息
find_package(OpenCV 4.2 REQUIRED)

# 添加项目包含路径
include_directories(${OpenCV_INCLUDE_DIRS} include)

# 用源文件为工程添加可执行文件，名字和项目名称一致
add_executable(feature_match source/feature_matcher.cpp source/vfc.cpp)

# 可执行文件添加库链接
target_link_libraries(feature_match ${OpenCV_LIBS})
MESSAGE("OpenCV_LIBS: " ${OpenCV_LIBS} )
