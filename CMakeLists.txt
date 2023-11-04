cmake_minimum_required(VERSION 3.10) # due to googletest

project(fempcli
    LANGUAGES CXX
    VERSION 0.1.0
)

find_package(Boost REQUIRED COMPONENTS program_options)

add_subdirectory(external)
add_subdirectory(src)

option(BUILD_TESTING "Runs tests" ON)
option(FEMPCLI_BUILD_TESTING "Runs tests" ON)
if(BUILD_TESTING AND FEMPCLI_BUILD_TESTING)
	find_package(GTest CONFIG REQUIRED)

    enable_testing()
    add_subdirectory(tests)
endif()
