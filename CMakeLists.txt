cmake_minimum_required(VERSION 3.12)

include("./CMakeShared.txt")

set(PROJ_NAME pr_sqlite)

project(${PROJ_NAME} CXX)

# set(PRECOMPILED_HEADER "stdafx")

link_external_library(sqlite)
link_external_library(vfilesystem)
link_external_library(sharedutils)
link_external_library(mathutil)
link_external_library(ishared)
add_external_library(luajit)
if(WIN32)
	add_external_library(lua)
endif()
add_include_dir(glm)

link_generic_module_libraries()
register_pragma_module(${PROJ_NAME})

add_subdirectory(third_party/sqlite)
set_target_properties(SQLite3 PROPERTIES FOLDER third_party)
add_dependencies(${PROJ_NAME} SQLite3)
