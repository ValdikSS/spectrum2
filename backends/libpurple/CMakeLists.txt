cmake_minimum_required(VERSION 2.6)
FILE(GLOB SRC *.cpp)

ADD_EXECUTABLE(spectrum2_libpurple_backend ${SRC})

if(MSVC)
target_link_libraries(spectrum2_libpurple_backend transport ${PURPLE_LIBRARY} ${GLIB2_LIBRARIES} ${LIBXML2_LIBRARIES} ${EVENT_LIBRARIES} transport-plugin ${PROTOBUF_LIBRARY})
else()
	if (NOT WIN32)
	target_link_libraries(spectrum2_libpurple_backend transport ${PURPLE_LIBRARY} ${GLIB2_LIBRARIES} ${EVENT_LIBRARIES} transport-plugin pthread)
	else()
	target_link_libraries(spectrum2_libpurple_backend transport ${PURPLE_LIBRARY} ${GLIB2_LIBRARIES} ${EVENT_LIBRARIES} transport-plugin)
	endif()
endif()

INSTALL(TARGETS spectrum2_libpurple_backend RUNTIME DESTINATION bin)

