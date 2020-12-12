# Suprisingly failing CMake dependencies
```
rm -rf build && mkdir build && cd build
```

```
cmake .. -D CMAKE_CXX_COMPILER=clang++ -DCMAKE_CXX_FLAGS=-fuse-ld=lld && make
```

```
make clean && cmake .. -D CMAKE_CXX_COMPILER=g++-9 && make
```

First successful build with clang++, then failed build with g++. What happened?

Surprise failure (undefined reference) happens because the transitive dependencies are located as the last ones in the linker command line (after the "utils3" that we thought would be the last), and ld is pretty dumb; it forgets the libraries it has seen before.

There is a trick around this in the comments of the root CMakeLists.txt. Real solution would be to declare the dependency for the library where it is needed. But sometimes you might not be able to do that.
