## Add libraries
set(HUNTER_BASE_SRC 
    src/hunter_base.cpp
    src/hunter_can_parser.cpp
    src/hunter_serial_parser.cpp
)
add_library(hunterbase STATIC ${HUNTER_BASE_SRC})
set_target_properties(hunterbase PROPERTIES POSITION_INDEPENDENT_CODE ON)
target_link_libraries(hunterbase asyncio agilex_protocol)
target_include_directories(hunterbase PUBLIC
    $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}/include>
    $<BUILD_INTERFACE:${Boost_INCLUDE_DIRS}>
	$<INSTALL_INTERFACE:include>	
    PRIVATE src)

 ## Add executables
# if(BUILD_TESTS)
#     add_subdirectory(tests)
# endif()