cmake_minimum_required(VERSION 3.21)

#**************************************************************************************************
# Project *****************************************************************************************
project(openframeworks)

include(CMakePackageConfigHelpers)

#**************************************************************************************************
# Include *****************************************************************************************
include_directories(${CMAKE_CURRENT_SOURCE_DIR}/src)

# get_cmake_property(_variableNames VARIABLES)
# list (SORT _variableNames)
# foreach (_variableName ${_variableNames})
#     message(STATUS "${_variableName}=${${_variableName}}")
# endforeach()

#**************************************************************************************************
# Set compiler ************************************************************************************
set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED TRUE)

if (CMAKE_SYSTEM_NAME STREQUAL "Windows")
  add_compile_options(/Oy /utf-8 /Zc:__cplusplus /DUNICODE /D_UNICODE)
else()
  add_compile_options(-fPIC -O3 -fno-omit-frame-pointer)
endif()

set(OPENFRAMEWORK_SRC
  ${CMAKE_CURRENT_SOURCE_DIR}/libs/openFrameworks/3d/of3dPrimitives.cpp
  ${CMAKE_CURRENT_SOURCE_DIR}/libs/openFrameworks/3d/of3dUtils.cpp
  ${CMAKE_CURRENT_SOURCE_DIR}/libs/openFrameworks/3d/ofCamera.cpp
  ${CMAKE_CURRENT_SOURCE_DIR}/libs/openFrameworks/3d/ofEasyCam.cpp
  ${CMAKE_CURRENT_SOURCE_DIR}/libs/openFrameworks/3d/ofNode.cpp
  # ${CMAKE_CURRENT_SOURCE_DIR}/libs/openFrameworks/app/ofAppEGLWindow.cpp
  ${CMAKE_CURRENT_SOURCE_DIR}/libs/openFrameworks/app/ofAppGLFWWindow.cpp
  ${CMAKE_CURRENT_SOURCE_DIR}/libs/openFrameworks/app/ofAppGlutWindow.cpp
  ${CMAKE_CURRENT_SOURCE_DIR}/libs/openFrameworks/app/ofAppNoWindow.cpp
  ${CMAKE_CURRENT_SOURCE_DIR}/libs/openFrameworks/app/ofAppRunner.cpp
  ${CMAKE_CURRENT_SOURCE_DIR}/libs/openFrameworks/app/ofBaseApp.cpp
  ${CMAKE_CURRENT_SOURCE_DIR}/libs/openFrameworks/app/ofMainLoop.cpp
  ${CMAKE_CURRENT_SOURCE_DIR}/libs/openFrameworks/communication/ofArduino.cpp
  ${CMAKE_CURRENT_SOURCE_DIR}/libs/openFrameworks/communication/ofSerial.cpp
  ${CMAKE_CURRENT_SOURCE_DIR}/libs/openFrameworks/events/ofEvents.cpp
  ${CMAKE_CURRENT_SOURCE_DIR}/libs/openFrameworks/gl/ofBufferObject.cpp
  ${CMAKE_CURRENT_SOURCE_DIR}/libs/openFrameworks/gl/ofFbo.cpp
  ${CMAKE_CURRENT_SOURCE_DIR}/libs/openFrameworks/gl/ofGLProgrammableRenderer.cpp
  ${CMAKE_CURRENT_SOURCE_DIR}/libs/openFrameworks/gl/ofGLRenderer.cpp
  ${CMAKE_CURRENT_SOURCE_DIR}/libs/openFrameworks/gl/ofGLUtils.cpp
  ${CMAKE_CURRENT_SOURCE_DIR}/libs/openFrameworks/gl/ofLight.cpp
  ${CMAKE_CURRENT_SOURCE_DIR}/libs/openFrameworks/gl/ofMaterial.cpp
  ${CMAKE_CURRENT_SOURCE_DIR}/libs/openFrameworks/gl/ofShader.cpp
  ${CMAKE_CURRENT_SOURCE_DIR}/libs/openFrameworks/gl/ofTexture.cpp
  ${CMAKE_CURRENT_SOURCE_DIR}/libs/openFrameworks/gl/ofVbo.cpp
  ${CMAKE_CURRENT_SOURCE_DIR}/libs/openFrameworks/gl/ofVboMesh.cpp
  ${CMAKE_CURRENT_SOURCE_DIR}/libs/openFrameworks/graphics/of3dGraphics.cpp
  ${CMAKE_CURRENT_SOURCE_DIR}/libs/openFrameworks/graphics/ofBitmapFont.cpp
  ${CMAKE_CURRENT_SOURCE_DIR}/libs/openFrameworks/graphics/ofCairoRenderer.cpp
  ${CMAKE_CURRENT_SOURCE_DIR}/libs/openFrameworks/graphics/ofGraphics.cpp
  ${CMAKE_CURRENT_SOURCE_DIR}/libs/openFrameworks/graphics/ofGraphicsBaseTypes.cpp
  ${CMAKE_CURRENT_SOURCE_DIR}/libs/openFrameworks/graphics/ofImage.cpp
  ${CMAKE_CURRENT_SOURCE_DIR}/libs/openFrameworks/graphics/ofPath.cpp
  ${CMAKE_CURRENT_SOURCE_DIR}/libs/openFrameworks/graphics/ofPixels.cpp
  ${CMAKE_CURRENT_SOURCE_DIR}/libs/openFrameworks/graphics/ofRendererCollection.cpp
  ${CMAKE_CURRENT_SOURCE_DIR}/libs/openFrameworks/graphics/ofTessellator.cpp
  ${CMAKE_CURRENT_SOURCE_DIR}/libs/openFrameworks/graphics/ofTrueTypeFont.cpp
  ${CMAKE_CURRENT_SOURCE_DIR}/libs/openFrameworks/math/ofMath.cpp
  ${CMAKE_CURRENT_SOURCE_DIR}/libs/openFrameworks/math/ofMatrix3x3.cpp
  ${CMAKE_CURRENT_SOURCE_DIR}/libs/openFrameworks/math/ofMatrix4x4.cpp
  ${CMAKE_CURRENT_SOURCE_DIR}/libs/openFrameworks/math/ofQuaternion.cpp
  ${CMAKE_CURRENT_SOURCE_DIR}/libs/openFrameworks/math/ofVec2f.cpp
  ${CMAKE_CURRENT_SOURCE_DIR}/libs/openFrameworks/math/ofVec4f.cpp
  # ${CMAKE_CURRENT_SOURCE_DIR}/libs/openFrameworks/sound/ofFmodSoundPlayer.cpp
  ${CMAKE_CURRENT_SOURCE_DIR}/libs/openFrameworks/sound/ofOpenALSoundPlayer.cpp
  ${CMAKE_CURRENT_SOURCE_DIR}/libs/openFrameworks/sound/ofRtAudioSoundStream.cpp
  ${CMAKE_CURRENT_SOURCE_DIR}/libs/openFrameworks/sound/ofSoundBaseTypes.cpp
  ${CMAKE_CURRENT_SOURCE_DIR}/libs/openFrameworks/sound/ofSoundBuffer.cpp
  ${CMAKE_CURRENT_SOURCE_DIR}/libs/openFrameworks/sound/ofSoundPlayer.cpp
  ${CMAKE_CURRENT_SOURCE_DIR}/libs/openFrameworks/sound/ofSoundStream.cpp
  ${CMAKE_CURRENT_SOURCE_DIR}/libs/openFrameworks/types/ofBaseTypes.cpp
  ${CMAKE_CURRENT_SOURCE_DIR}/libs/openFrameworks/types/ofColor.cpp
  ${CMAKE_CURRENT_SOURCE_DIR}/libs/openFrameworks/types/ofParameter.cpp
  ${CMAKE_CURRENT_SOURCE_DIR}/libs/openFrameworks/types/ofParameterGroup.cpp
  ${CMAKE_CURRENT_SOURCE_DIR}/libs/openFrameworks/types/ofRectangle.cpp
  ${CMAKE_CURRENT_SOURCE_DIR}/libs/openFrameworks/utils/ofFileUtils.cpp
  ${CMAKE_CURRENT_SOURCE_DIR}/libs/openFrameworks/utils/ofFpsCounter.cpp
  ${CMAKE_CURRENT_SOURCE_DIR}/libs/openFrameworks/utils/ofLog.cpp
  ${CMAKE_CURRENT_SOURCE_DIR}/libs/openFrameworks/utils/ofMatrixStack.cpp
  ${CMAKE_CURRENT_SOURCE_DIR}/libs/openFrameworks/utils/ofSystemUtils.cpp
  ${CMAKE_CURRENT_SOURCE_DIR}/libs/openFrameworks/utils/ofThread.cpp
  ${CMAKE_CURRENT_SOURCE_DIR}/libs/openFrameworks/utils/ofTimer.cpp
  ${CMAKE_CURRENT_SOURCE_DIR}/libs/openFrameworks/utils/ofURLFileLoader.cpp
  ${CMAKE_CURRENT_SOURCE_DIR}/libs/openFrameworks/utils/ofUtils.cpp
  ${CMAKE_CURRENT_SOURCE_DIR}/libs/openFrameworks/utils/ofXml.cpp
  # ${CMAKE_CURRENT_SOURCE_DIR}/libs/openFrameworks/video/ofDirectShowGrabber.cpp
  ${CMAKE_CURRENT_SOURCE_DIR}/libs/openFrameworks/video/ofDirectShowPlayer.cpp
  ${CMAKE_CURRENT_SOURCE_DIR}/libs/openFrameworks/video/ofGstUtils.cpp
  ${CMAKE_CURRENT_SOURCE_DIR}/libs/openFrameworks/video/ofGstVideoGrabber.cpp
  ${CMAKE_CURRENT_SOURCE_DIR}/libs/openFrameworks/video/ofGstVideoPlayer.cpp
  # ${CMAKE_CURRENT_SOURCE_DIR}/libs/openFrameworks/video/ofQtUtils.cpp
  # ${CMAKE_CURRENT_SOURCE_DIR}/libs/openFrameworks/video/ofQuickTimeGrabber.cpp
  # ${CMAKE_CURRENT_SOURCE_DIR}/libs/openFrameworks/video/ofQuickTimePlayer.cpp
  ${CMAKE_CURRENT_SOURCE_DIR}/libs/openFrameworks/video/ofVideoGrabber.cpp
  ${CMAKE_CURRENT_SOURCE_DIR}/libs/openFrameworks/video/ofVideoPlayer.cpp

  # Addons
  # ofxGui
  ${CMAKE_CURRENT_SOURCE_DIR}/addons/ofxGui/src/ofxBaseGui.cpp
  ${CMAKE_CURRENT_SOURCE_DIR}/addons/ofxGui/src/ofxButton.cpp
  ${CMAKE_CURRENT_SOURCE_DIR}/addons/ofxGui/src/ofxColorPicker.cpp
  ${CMAKE_CURRENT_SOURCE_DIR}/addons/ofxGui/src/ofxGuiGroup.cpp
  ${CMAKE_CURRENT_SOURCE_DIR}/addons/ofxGui/src/ofxInputField.cpp
  ${CMAKE_CURRENT_SOURCE_DIR}/addons/ofxGui/src/ofxLabel.cpp
  ${CMAKE_CURRENT_SOURCE_DIR}/addons/ofxGui/src/ofxPanel.cpp
  ${CMAKE_CURRENT_SOURCE_DIR}/addons/ofxGui/src/ofxSlider.cpp
  ${CMAKE_CURRENT_SOURCE_DIR}/addons/ofxGui/src/ofxSliderGroup.cpp
  ${CMAKE_CURRENT_SOURCE_DIR}/addons/ofxGui/src/ofxToggle.cpp
)

set(OPENFRAMEWORK_HEADERS
  ${CMAKE_CURRENT_SOURCE_DIR}/libs/openFrameworks/3d/of3dPrimitives.h
  ${CMAKE_CURRENT_SOURCE_DIR}/libs/openFrameworks/3d/of3dUtils.h
  ${CMAKE_CURRENT_SOURCE_DIR}/libs/openFrameworks/3d/ofCamera.h
  ${CMAKE_CURRENT_SOURCE_DIR}/libs/openFrameworks/3d/ofEasyCam.h
  ${CMAKE_CURRENT_SOURCE_DIR}/libs/openFrameworks/3d/ofMesh.h
  ${CMAKE_CURRENT_SOURCE_DIR}/libs/openFrameworks/3d/ofMesh.inl
  ${CMAKE_CURRENT_SOURCE_DIR}/libs/openFrameworks/3d/ofNode.h
  ${CMAKE_CURRENT_SOURCE_DIR}/libs/openFrameworks/app/ofAppBaseWindow.h
  # ${CMAKE_CURRENT_SOURCE_DIR}/libs/openFrameworks/app/ofAppEGLWindow.h
  ${CMAKE_CURRENT_SOURCE_DIR}/libs/openFrameworks/app/ofAppGLFWWindow.h
  ${CMAKE_CURRENT_SOURCE_DIR}/libs/openFrameworks/app/ofAppGlutWindow.h
  ${CMAKE_CURRENT_SOURCE_DIR}/libs/openFrameworks/app/ofAppNoWindow.h
  ${CMAKE_CURRENT_SOURCE_DIR}/libs/openFrameworks/app/ofAppRunner.h
  ${CMAKE_CURRENT_SOURCE_DIR}/libs/openFrameworks/app/ofBaseApp.h
  ${CMAKE_CURRENT_SOURCE_DIR}/libs/openFrameworks/app/ofIcon.h
  ${CMAKE_CURRENT_SOURCE_DIR}/libs/openFrameworks/app/ofMainLoop.h
  ${CMAKE_CURRENT_SOURCE_DIR}/libs/openFrameworks/app/ofWindowSettings.h
  ${CMAKE_CURRENT_SOURCE_DIR}/libs/openFrameworks/communication/ofArduino.h
  ${CMAKE_CURRENT_SOURCE_DIR}/libs/openFrameworks/communication/ofSerial.h
  ${CMAKE_CURRENT_SOURCE_DIR}/libs/openFrameworks/events/ofEvent.h
  ${CMAKE_CURRENT_SOURCE_DIR}/libs/openFrameworks/events/ofEvents.h
  ${CMAKE_CURRENT_SOURCE_DIR}/libs/openFrameworks/events/ofEventUtils.h
  ${CMAKE_CURRENT_SOURCE_DIR}/libs/openFrameworks/gl/ofBufferObject.h
  ${CMAKE_CURRENT_SOURCE_DIR}/libs/openFrameworks/gl/ofFbo.h
  ${CMAKE_CURRENT_SOURCE_DIR}/libs/openFrameworks/gl/ofGLBaseTypes.h
  ${CMAKE_CURRENT_SOURCE_DIR}/libs/openFrameworks/gl/ofGLProgrammableRenderer.h
  ${CMAKE_CURRENT_SOURCE_DIR}/libs/openFrameworks/gl/ofGLRenderer.h
  ${CMAKE_CURRENT_SOURCE_DIR}/libs/openFrameworks/gl/ofGLUtils.h
  ${CMAKE_CURRENT_SOURCE_DIR}/libs/openFrameworks/gl/ofLight.h
  ${CMAKE_CURRENT_SOURCE_DIR}/libs/openFrameworks/gl/ofMaterial.h
  ${CMAKE_CURRENT_SOURCE_DIR}/libs/openFrameworks/gl/ofShader.h
  ${CMAKE_CURRENT_SOURCE_DIR}/libs/openFrameworks/gl/ofTexture.h
  ${CMAKE_CURRENT_SOURCE_DIR}/libs/openFrameworks/gl/ofVbo.h
  ${CMAKE_CURRENT_SOURCE_DIR}/libs/openFrameworks/gl/ofVboMesh.h
  ${CMAKE_CURRENT_SOURCE_DIR}/libs/openFrameworks/graphics/of3dGraphics.h
  ${CMAKE_CURRENT_SOURCE_DIR}/libs/openFrameworks/graphics/ofBitmapFont.h
  ${CMAKE_CURRENT_SOURCE_DIR}/libs/openFrameworks/graphics/ofCairoRenderer.h
  ${CMAKE_CURRENT_SOURCE_DIR}/libs/openFrameworks/graphics/ofGraphics.h
  ${CMAKE_CURRENT_SOURCE_DIR}/libs/openFrameworks/graphics/ofGraphicsBaseTypes.h
  ${CMAKE_CURRENT_SOURCE_DIR}/libs/openFrameworks/graphics/ofGraphicsConstants.h
  ${CMAKE_CURRENT_SOURCE_DIR}/libs/openFrameworks/graphics/ofImage.h
  ${CMAKE_CURRENT_SOURCE_DIR}/libs/openFrameworks/graphics/ofPath.h
  ${CMAKE_CURRENT_SOURCE_DIR}/libs/openFrameworks/graphics/ofPixels.h
  ${CMAKE_CURRENT_SOURCE_DIR}/libs/openFrameworks/graphics/ofPolyline.h
  ${CMAKE_CURRENT_SOURCE_DIR}/libs/openFrameworks/graphics/ofPolyline.inl
  ${CMAKE_CURRENT_SOURCE_DIR}/libs/openFrameworks/graphics/ofRendererCollection.h
  ${CMAKE_CURRENT_SOURCE_DIR}/libs/openFrameworks/graphics/ofTessellator.h
  ${CMAKE_CURRENT_SOURCE_DIR}/libs/openFrameworks/graphics/ofTrueTypeFont.h
  ${CMAKE_CURRENT_SOURCE_DIR}/libs/openFrameworks/math/ofMath.h
  ${CMAKE_CURRENT_SOURCE_DIR}/libs/openFrameworks/math/ofMathConstants.h
  ${CMAKE_CURRENT_SOURCE_DIR}/libs/openFrameworks/math/ofMatrix3x3.h
  ${CMAKE_CURRENT_SOURCE_DIR}/libs/openFrameworks/math/ofMatrix4x4.h
  ${CMAKE_CURRENT_SOURCE_DIR}/libs/openFrameworks/math/ofQuaternion.h
  ${CMAKE_CURRENT_SOURCE_DIR}/libs/openFrameworks/math/ofVec2f.h
  ${CMAKE_CURRENT_SOURCE_DIR}/libs/openFrameworks/math/ofVec3f.h
  ${CMAKE_CURRENT_SOURCE_DIR}/libs/openFrameworks/math/ofVec4f.h
  ${CMAKE_CURRENT_SOURCE_DIR}/libs/openFrameworks/math/ofVectorMath.h
  ${CMAKE_CURRENT_SOURCE_DIR}/libs/openFrameworks/ofMain.h
  # ${CMAKE_CURRENT_SOURCE_DIR}/libs/openFrameworks/sound/ofFmodSoundPlayer.h
  ${CMAKE_CURRENT_SOURCE_DIR}/libs/openFrameworks/sound/ofOpenALSoundPlayer.h
  ${CMAKE_CURRENT_SOURCE_DIR}/libs/openFrameworks/sound/ofRtAudioSoundStream.h
  ${CMAKE_CURRENT_SOURCE_DIR}/libs/openFrameworks/sound/ofSoundBaseTypes.h
  ${CMAKE_CURRENT_SOURCE_DIR}/libs/openFrameworks/sound/ofSoundBuffer.h
  ${CMAKE_CURRENT_SOURCE_DIR}/libs/openFrameworks/sound/ofSoundPlayer.h
  ${CMAKE_CURRENT_SOURCE_DIR}/libs/openFrameworks/sound/ofSoundStream.h
  ${CMAKE_CURRENT_SOURCE_DIR}/libs/openFrameworks/sound/ofSoundUtils.h
  ${CMAKE_CURRENT_SOURCE_DIR}/libs/openFrameworks/types/ofBaseTypes.h
  ${CMAKE_CURRENT_SOURCE_DIR}/libs/openFrameworks/types/ofColor.h
  ${CMAKE_CURRENT_SOURCE_DIR}/libs/openFrameworks/types/ofParameter.h
  ${CMAKE_CURRENT_SOURCE_DIR}/libs/openFrameworks/types/ofParameterGroup.h
  ${CMAKE_CURRENT_SOURCE_DIR}/libs/openFrameworks/types/ofPoint.h
  ${CMAKE_CURRENT_SOURCE_DIR}/libs/openFrameworks/types/ofRectangle.h
  ${CMAKE_CURRENT_SOURCE_DIR}/libs/openFrameworks/types/ofTypes.h
  ${CMAKE_CURRENT_SOURCE_DIR}/libs/openFrameworks/utils/ofConstants.h
  ${CMAKE_CURRENT_SOURCE_DIR}/libs/openFrameworks/utils/ofFileUtils.h
  ${CMAKE_CURRENT_SOURCE_DIR}/libs/openFrameworks/utils/ofFpsCounter.h
  ${CMAKE_CURRENT_SOURCE_DIR}/libs/openFrameworks/utils/ofJson.h
  ${CMAKE_CURRENT_SOURCE_DIR}/libs/openFrameworks/utils/ofLog.h
  ${CMAKE_CURRENT_SOURCE_DIR}/libs/openFrameworks/utils/ofMatrixStack.h
  ${CMAKE_CURRENT_SOURCE_DIR}/libs/openFrameworks/utils/ofNoise.h
  ${CMAKE_CURRENT_SOURCE_DIR}/libs/openFrameworks/utils/ofSystemUtils.h
  ${CMAKE_CURRENT_SOURCE_DIR}/libs/openFrameworks/utils/ofThread.h
  ${CMAKE_CURRENT_SOURCE_DIR}/libs/openFrameworks/utils/ofThreadChannel.h
  ${CMAKE_CURRENT_SOURCE_DIR}/libs/openFrameworks/utils/ofTimer.h
  ${CMAKE_CURRENT_SOURCE_DIR}/libs/openFrameworks/utils/ofURLFileLoader.h
  ${CMAKE_CURRENT_SOURCE_DIR}/libs/openFrameworks/utils/ofUtils.h
  ${CMAKE_CURRENT_SOURCE_DIR}/libs/openFrameworks/utils/ofXml.h
  ${CMAKE_CURRENT_SOURCE_DIR}/libs/openFrameworks/video/ofAVFoundationGrabber.h
  ${CMAKE_CURRENT_SOURCE_DIR}/libs/openFrameworks/video/ofAVFoundationPlayer.h
  ${CMAKE_CURRENT_SOURCE_DIR}/libs/openFrameworks/video/ofAVFoundationVideoPlayer.h
  # ${CMAKE_CURRENT_SOURCE_DIR}/libs/openFrameworks/video/ofDirectShowGrabber.h
  ${CMAKE_CURRENT_SOURCE_DIR}/libs/openFrameworks/video/ofDirectShowPlayer.h
  ${CMAKE_CURRENT_SOURCE_DIR}/libs/openFrameworks/video/ofGstUtils.h
  ${CMAKE_CURRENT_SOURCE_DIR}/libs/openFrameworks/video/ofGstVideoGrabber.h
  ${CMAKE_CURRENT_SOURCE_DIR}/libs/openFrameworks/video/ofGstVideoPlayer.h
  ${CMAKE_CURRENT_SOURCE_DIR}/libs/openFrameworks/video/ofQTKitGrabber.h
  ${CMAKE_CURRENT_SOURCE_DIR}/libs/openFrameworks/video/ofQTKitMovieRenderer.h
  ${CMAKE_CURRENT_SOURCE_DIR}/libs/openFrameworks/video/ofQTKitPlayer.h
  # ${CMAKE_CURRENT_SOURCE_DIR}/libs/openFrameworks/video/ofQtUtils.h
  # ${CMAKE_CURRENT_SOURCE_DIR}/libs/openFrameworks/video/ofQuickTimeGrabber.h
  # ${CMAKE_CURRENT_SOURCE_DIR}/libs/openFrameworks/video/ofQuickTimePlayer.h
  ${CMAKE_CURRENT_SOURCE_DIR}/libs/openFrameworks/video/ofVideoBaseTypes.h
  ${CMAKE_CURRENT_SOURCE_DIR}/libs/openFrameworks/video/ofVideoGrabber.h
  ${CMAKE_CURRENT_SOURCE_DIR}/libs/openFrameworks/video/ofVideoPlayer.h

  # Addons
  # ofxGui
  ${CMAKE_CURRENT_SOURCE_DIR}/addons/ofxGui/src/ofxBaseGui.h
  ${CMAKE_CURRENT_SOURCE_DIR}/addons/ofxGui/src/ofxButton.h
  ${CMAKE_CURRENT_SOURCE_DIR}/addons/ofxGui/src/ofxColorPicker.h
  ${CMAKE_CURRENT_SOURCE_DIR}/addons/ofxGui/src/ofxGui.h
  ${CMAKE_CURRENT_SOURCE_DIR}/addons/ofxGui/src/ofxGuiGroup.h
  ${CMAKE_CURRENT_SOURCE_DIR}/addons/ofxGui/src/ofxGuiUtils.h
  ${CMAKE_CURRENT_SOURCE_DIR}/addons/ofxGui/src/ofxInputField.h
  ${CMAKE_CURRENT_SOURCE_DIR}/addons/ofxGui/src/ofxLabel.h
  ${CMAKE_CURRENT_SOURCE_DIR}/addons/ofxGui/src/ofxPanel.h
  ${CMAKE_CURRENT_SOURCE_DIR}/addons/ofxGui/src/ofxSlider.h
  ${CMAKE_CURRENT_SOURCE_DIR}/addons/ofxGui/src/ofxSliderGroup.h
  ${CMAKE_CURRENT_SOURCE_DIR}/addons/ofxGui/src/ofxToggle.h
)

add_library(openframework STATIC ${OPENFRAMEWORK_SRC})

add_compile_definitions(OF_USING_STD_FS 1)
add_compile_definitions(OF_SOUND_PLAYER_OPENAL 1)

# Include Openframework headers
target_include_directories(openframework PUBLIC
  $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}/libs/openFrameworks>
  $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}/libs/openFrameworks/3d>
  $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}/libs/openFrameworks/app>
  $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}/libs/openFrameworks/communication>
  $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}/libs/openFrameworks/events>
  $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}/libs/openFrameworks/gl>
  $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}/libs/openFrameworks/graphics>
  $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}/libs/openFrameworks/math>
  $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}/libs/openFrameworks/sound>
  $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}/libs/openFrameworks/types>
  $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}/libs/openFrameworks/utils>
  $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}/libs/openFrameworks/video>
  $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}/addons/ofxGui/src>
  $<INSTALL_INTERFACE:${CMAKE_INSTALL_INCLUDEDIR}>
)

# Include Openframework dependency headers
find_package(libpng CONFIG REQUIRED)
target_link_libraries(openframework PUBLIC png)

find_package(CURL CONFIG REQUIRED)
target_link_libraries(openframework PUBLIC CURL::libcurl)

find_package(OpenGL REQUIRED)
target_link_libraries(openframework PUBLIC ${OPENGL_gl_LIBRARY})

find_package(GLEW REQUIRED)
target_link_libraries(openframework PUBLIC GLEW::GLEW)

find_package(glm CONFIG REQUIRED)
target_link_libraries(openframework PUBLIC glm::glm)

find_package(pugixml CONFIG REQUIRED)
target_link_libraries(openframework PUBLIC pugixml pugixml::shared pugixml::pugixml)

find_package(ZLIB REQUIRED)
target_link_libraries(openframework PUBLIC ZLIB::ZLIB)

find_package(nlohmann_json CONFIG REQUIRED)
target_link_libraries(openframework PUBLIC nlohmann_json::nlohmann_json)
target_include_directories(openframework PUBLIC ${_VCPKG_INSTALLED_DIR}/${VCPKG_TARGET_TRIPLET}/include/nlohmann)

find_package(uriparser CONFIG REQUIRED)
target_link_libraries(openframework PUBLIC uriparser::uriparser)

find_package(utf8cpp CONFIG REQUIRED)
target_link_libraries(openframework PUBLIC utf8cpp)

find_package(glfw3 CONFIG REQUIRED)
target_link_libraries(openframework PUBLIC glfw)

find_package(freetype CONFIG REQUIRED)
target_link_libraries(openframework PUBLIC freetype)

find_package(freeimage CONFIG REQUIRED)
target_link_libraries(openframework PUBLIC freeimage::FreeImage freeimage::FreeImagePlus)

find_package(RtAudio CONFIG REQUIRED)
target_link_libraries(openframework PUBLIC RtAudio::rtaudio)

find_package(unofficial-kissfft CONFIG REQUIRED)
target_link_libraries(openframework PUBLIC unofficial::kissfft::kissfft)

find_package(unofficial-libtess2 CONFIG REQUIRED)
target_link_libraries(openframework PUBLIC unofficial::libtess2::libtess2)

find_package(OpenAL CONFIG REQUIRED)
target_link_libraries(openframework PUBLIC OpenAL::OpenAL)

find_package(SndFile CONFIG REQUIRED)
target_link_libraries(openframework PUBLIC SndFile::sndfile)

find_library(CAIRO_LIB cairo REQUIRED)
target_link_libraries(openframework PUBLIC ${CAIRO_LIB})
target_include_directories(openframework PUBLIC ${_VCPKG_INSTALLED_DIR}/${VCPKG_TARGET_TRIPLET}/include/cairo)

target_include_directories(openframework PUBLIC ${_VCPKG_INSTALLED_DIR}/${VCPKG_TARGET_TRIPLET}/include/GL)

target_include_directories(openframework PUBLIC ${_VCPKG_INSTALLED_DIR}/${VCPKG_TARGET_TRIPLET}/include/gstreamer-1.0)
target_include_directories(openframework PUBLIC ${_VCPKG_INSTALLED_DIR}/${VCPKG_TARGET_TRIPLET}/include/glib-2.0)
target_include_directories(openframework PUBLIC ${_VCPKG_INSTALLED_DIR}/${VCPKG_TARGET_TRIPLET}/lib/glib-2.0/include)

add_subdirectory(third-party)
target_link_libraries(openframework PUBLIC videoInput)

# install(FILES ${OPENFRAMEWORK_HEADERS}

# I can't use that header don't reference folder architecture, We have to flatten
# install(
#   DIRECTORY "${CMAKE_CURRENT_SOURCE_DIR}/libs/openFrameworks" # source directory
#   TYPE INCLUDE
#   FILES_MATCHING # install only matched files
#   PATTERN "*.h" # select header files
# )

install(
  FILES ${OPENFRAMEWORK_HEADERS}
  TYPE INCLUDE
)

install(
  TARGETS openframework
  EXPORT unofficial-openframework-config
)

install(
  EXPORT unofficial-openframework-config
  NAMESPACE unofficial::openframework::
  DESTINATION ${CMAKE_INSTALL_LIBDIR}/cmake/unofficial-openframework
  PERMISSIONS OWNER_READ OWNER_WRITE GROUP_READ WORLD_READ
)


add_executable(example
  ${CMAKE_CURRENT_SOURCE_DIR}/examples/graphics/colorExample/src/main.cpp
  ${CMAKE_CURRENT_SOURCE_DIR}/examples/graphics/colorExample/src/ofApp.cpp
)

target_link_libraries(example PRIVATE openframework)
