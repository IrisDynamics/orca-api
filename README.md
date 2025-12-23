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

## Notes on Variable Names

Some of the registers of ORCA motors are broken down into individual bits or groups of bits which represent different pieces of information. An example is the ERROR_0 register, in which each bit represents a different error that the motor can encounter. These registers can be described as "bit fields", in which different collections of bits hold distinct meanings.

The term 'Mask' in the name of a variable refers to the bitmask for a subsection of a bit field register.

The term 'Shift' in the name of a variable refers to the left bit shift required to have a value correctly 'align' with the relevant subsection of a bit field.