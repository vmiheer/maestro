cmake_minimum_required (VERSION 3.17)
project (cmake_maestro)
set (CMAKE_CXX_STANDARD 17)

include_directories(.)
include_directories(./cost-model/include)
include_directories(./cost-model/include/base)
include_directories(./cost-model/include/tools)
include_directories(./cost-model/include/user-api)
include_directories(./cost-model/include/dataflow-analysis)
include_directories(./cost-model/include/dataflow-specification-language)
include_directories(./cost-model/include/design-space-exploration)
include_directories(./cost-model/include/cost-analysis)
include_directories(./cost-model/include/abstract-hardware-model)
include_directories(./cost-model/include/flexibility-evaluation)
include_directories(./cost-model/src)

find_package(OpenMP REQUIRED)

set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(Boost_USE_STATIC_LIBS OFF)
set(Boost_USE_MULTITHREADED ON)
set(Boost_USE_STATIC_RUNTIME OFF)
find_package(Boost COMPONENTS filesystem system program_options)
include_directories(${Boost_INCLUDE_DIRS})


#set (CMAKE_EXE_LINKER_FLAGS "${CMAKE_EXE_LINKER_FLAGS} -lomp")
add_executable (${PROJECT_NAME} maestro-top.cpp
        ./cost-model/src/BASE_base-objects.cpp
        )
target_link_libraries(${PROJECT_NAME} ${Boost_LIBRARIES} OpenMP::OpenMP_CXX)

