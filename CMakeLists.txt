cmake_minimum_required (VERSION 2.8.11)
project (cmake-surprise)

add_subdirectory(utils)

add_executable(example example.cpp)

target_link_libraries(example PRIVATE utils1 utils3)

# Hackish fix by replacing the previous line with: 
# add_library(proxy_utils3 INTERFACE)
# target_link_libraries(proxy_utils3 INTERFACE utils3)
# target_link_libraries(example PRIVATE utils1 proxy_utils3)
