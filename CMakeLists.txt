cmake_minimum_required(VERSION 3.11)
Project(PersonenServiceProjekt)
enable_testing()
set(CMAKE_CXX_FLAGS_RELEASE "${CMAKE_CXX_FLAGS_RELEASE} /MT")
set(CMAKE_CXX_FLAGS_DEBUG "${CMAKE_CXX_FLAGS_DEBUG} /MTd")
set(CMAKE_CXX_STANDARD 17)
include(FetchContent)
FetchContent_Declare(
  googletest
  GIT_REPOSITORY https://github.com/google/googletest.git
  GIT_TAG        release-1.10.0
)
FetchContent_GetProperties(googletest)
if(NOT googletest_POPULATED)
  FetchContent_Populate(googletest)
  add_subdirectory(${googletest_SOURCE_DIR} ${googletest_BINARY_DIR})
endif()
add_executable(PersonenServiceProjekt 
Person.cpp
PersonenServiceProjekt.cpp
pch.cpp
person_service_impl.cpp
personen_service_exception.cpp)
target_link_libraries(PersonenServiceProjekt gtest gmock gtest_main)
add_test(PersonenServiceProjekt PersonenServiceProjekt)
