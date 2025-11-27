cmake_minimum_required(VERSION 3.23)

project(orcaAPI VERSION 1.0.0)

include(GNUInstallDirs)

# C and CPP header includes
add_library(orcaAPI_headers INTERFACE)
add_library(orcaAPI::orcaAPI ALIAS orcaAPI_headers)

target_sources(orcaAPI_headers
	PUBLIC
		FILE_SET publicAPI
		TYPE HEADERS
		FILES
			c/orca_registers.h
			cpp/orca_registers.hpp
)

set_target_properties(orcaAPI_headers
	PROPERTIES
		VERSION ${orcaAPI_VERSION}
		SOVERSION ${orcaAPI_VERSION_MAJOR}
	EXPORT_NAME orcaAPI
)

install(TARGETS orcaAPI_headers
	EXPORT orcaAPITargets
	FILE_SET publicAPI
)

install(EXPORT orcaAPITargets
	DESTINATION ${CMAKE_INSTALL_LIBDIR}/cmake/orcaAPI
	NAMESPACE orcaAPI::
)

# Project install
install(
	FILES 
		"orcaAPIConfig.cmake"
	DESTINATION
		"${CMAKE_INSTALL_LIBDIR}/cmake/orcaAPI"
)