cmake_minimum_required(VERSION 3.2.2)

project(pipTest)

set(googleTest_Dir ${CMAKE_CURRENT_SOURCE_DIR}/googletest)
if (EXISTS ${googleTest_Dir})
	SET(GTestSrc ${googleTest_Dir}/googletest)
	SET(GMockSrc ${googleTest_Dir}/googlemock)
else ()
	message(FATAL_ERROR "No googletest src dir found!")
endif ()
include_directories(${GTestSrc} ${GTestSrc}/include ${GMockSrc} ${GMockSrc}/include ${CMAKE_HOME_DIRECTORY} ${CMAKE_HOME_DIRECTORY}/test )

set(test_SOURCES
		main.cpp

		astar/NodeTest.cpp
		astar/NodeListTest.cpp
		)

set(test_HEADERS
		StandardInclude.h
		)

add_executable(pipTest ${test_SOURCES} ${test_HEADERS} ${GTestSrc}/src/gtest-all.cc ${GMockSrc}/src/gmock-all.cc)

target_link_libraries(pipTest astar pthread)
