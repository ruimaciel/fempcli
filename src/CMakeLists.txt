cmake_minimum_required(VERSION 3.10)

project(fempcli
    LANGUAGES CXX
    VERSION 0.1.0
    )

find_package( Boost REQUIRED COMPONENTS program_options)


set(fempcli_HEADERS
    commands/FempCommand.hpp
    commands/ErrorReportingCommand.hpp
    commands/HelpCommand.hpp
    commands/AnalysisCommand.hpp
    CliProgressIndicatorStrategy.hpp
    )

set(fempcli_SOURCES
    commands/FempCommand.cpp
    commands/ErrorReportingCommand.cpp
    commands/HelpCommand.cpp
    commands/AnalysisCommand.cpp
    CliProgressIndicatorStrategy.cpp
    main.cpp
    )

add_executable(fempcli
    ${fempcli_HEADERS}
    ${fempcli_SOURCES}
    )

target_link_libraries(fempcli
    libfemp::Static
    ${Boost_LIBRARIES}
    )

target_include_directories(fempcli
    PRIVATE 
	${CMAKE_CURRENT_SOURCE_DIR}
    )

set_target_properties(fempcli PROPERTIES
    CXX_STANDARD 14
    CXX_EXTENSIONS OFF
    )
