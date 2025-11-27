# ORCA API

This repository stores include files for various languages to describe the register API for ORCA series linear motors in forms that can be easily included in the programming languages we support.

## Including in C or C++

As this project is header only, including it in your C or C++ application can be as simple as downloading the appropriate header and placing it in an include directory for your project.

We also support CMake integration. The following is example CMake for including the API in your program:

``` CMakeLists.txt
...
find_package(orcaAPI)

add_executable(my_application)
target_link_libraries(my_application PUBLIC orcaAPI::orcaAPI)
...
```

This project supports both find_package and FetchContent.