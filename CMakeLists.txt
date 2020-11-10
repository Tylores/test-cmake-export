cmake_minimum_required(VERSION 3.15)
project(MathFunctions)

# specify the C++ standard
set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_STANDARD_REQUIRED True)

add_subdirectory(Addition)
add_subdirectory(SquareRoot)

add_library(MathFunctions STATIC MathFunctions.cxx)

target_include_directories(MathFunctions
                           PUBLIC
                           "$<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}>"
                           "$<INSTALL_INTERFACE:include>"
)

install(TARGETS MathFunctions
        EXPORT MathFunctionsTargets
        LIBRARY DESTINATION lib
        ARCHIVE DESTINATION lib
        RUNTIME DESTINATION bin
        INCLUDES DESTINATION include
)

install(FILES MathFunctions.h DESTINATION include)

install(EXPORT MathFunctionsTargets
        FILE MathFunctionsTargets.cmake
        NAMESPACE MathFunctions::
        DESTINATION lib/cmake
)


