cmake_minimum_required(VERSION 3.13.1)
include($ENV{ZEPHYR_BASE}/cmake/app/boilerplate.cmake NO_POLICY_SCOPE)
project(lmt)

target_include_directories(app PRIVATE $ENV{ZEPHYR_BASE}/drivers)
FILE(GLOB app_sources src/*.c)
target_sources(app PRIVATE ${app_sources})
if(TEST_CASE STREQUAL sleep-success)
    target_compile_definitions(app PRIVATE
	    -DTEST_CASE_SLEEP_SUCCESS
	)
endif()
