cmake_minimum_required(VERSION 3.16)

# UTF-8 source
add_compile_options("$<$<AND:$<C_COMPILER_ID:MSVC>,$<COMPILE_LANGUAGE:C>>:/utf-8>")
add_compile_options("$<$<AND:$<CXX_COMPILER_ID:MSVC>,$<COMPILE_LANGUAGE:CXX>>:/utf-8>")
add_compile_options("$<$<AND:$<CXX_COMPILER_ID:MSVC>,$<COMPILE_LANGUAGE:CXX>>:/Zc:__cplusplus>")

set(PROJECT_NAME httpserv)
set(PROJECT_VERSION 1.00)

project(${PROJECT_NAME} VERSION ${PROJECT_VERSION})

find_package(Poco REQUIRED COMPONENTS Foundation Util Net XML)

if(NOT TARGET ncbind)
add_subdirectory(../ncbind ${CMAKE_CURRENT_BINARY_DIR}/ncbind)
endif()

add_library(${PROJECT_NAME} SHARED
	serv.cpp
	main.cpp
)

target_link_libraries(${PROJECT_NAME} PUBLIC
	ncbind
	Poco::Foundation
	Poco::Util
	Poco::Net
	Poco::XML
)
