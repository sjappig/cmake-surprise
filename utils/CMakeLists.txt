add_library(utils3 utils3.cpp)

add_library(utils2 utils2.cpp)

add_library(utils1 utils1.cpp)

target_link_libraries(utils1 PRIVATE utils2)
