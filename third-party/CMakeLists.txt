
# VideoInput
set(VIDEOINPUT_SRC
  ${CMAKE_CURRENT_SOURCE_DIR}/videoInput/videoInputSrcAndDemos/libs/videoInput/videoInput.cpp
)
add_library(videoInput STATIC ${VIDEOINPUT_SRC})
target_include_directories(videoInput PUBLIC $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}/videoInput/videoInputSrcAndDemos/libs/videoInput>)
set_target_properties(videoInput PROPERTIES LINKER_LANGUAGE CXX)

install(TARGETS videoInput EXPORT unofficial-videoInput-config)

install(
    FILES ${CMAKE_CURRENT_SOURCE_DIR}/videoInput/videoInputSrcAndDemos/libs/videoInput/videoInput.h
    TYPE INCLUDE
)

install(
    EXPORT unofficial-videoInput-config
    NAMESPACE unofficial::videoInput::
    DESTINATION ${CMAKE_INSTALL_LIBDIR}/cmake/unofficial-videoInput
    PERMISSIONS OWNER_READ OWNER_WRITE GROUP_READ WORLD_READ
)