cmake_minimum_required(VERSION 3.3)

project(gpu_tool_utils)

set(src GrContextFactory.cpp GrTest.cpp MemoryCache.cpp MemoryCache.h ProxyUtils.cpp TestContext.cpp atlastext/GLTestAtlasTextRenderer.cpp gl/GLTestContext.cpp gl/command_buffer/GLTestContext_command_buffer.cpp gl/null/NullGLTestContext.cpp mock/MockTestContext.cpp)

set(lib)

set(is_android)

set(skia_use_egl)

if(DEFINED is_android OR DEFINED skia_use_egl)
    set(src ${src} gl/egl/CreatePlatformGLTestContext_egl.cpp)
elseif(DEFINED is_ios)
    set(src ${src} gl/iOS/CreatePlatformGLTestContext_iOS.mm)
    set(lib ${lib} OpenGLES.framework)
elseif(DEFINED is_linux)
    set(src ${src} gl/glx/CreatePlatformGLTestContext_glx.cpp)
    set(lib ${lib} GLU X11)
elseif(DEFINED is_mac)
    set(src ${src} gl/mac/CreatePlatformGLTestContext_mac.cpp)
elseif(DEFINED is_win)
    set(src ${src} gl/win/CreatePlatformGLTestContext_win.cpp)
    set(lib ${lib} Gdi32.lib OpenGL32.lib)
endif()

include_directories(/home/lonerr/Study/skia/tools/gpu /home/lonerr/Study/skia/third_party/vulkan /home/lonerr/Study/skia/include/private /home/lonerr/Study/skia/src/c /home/lonerr/Study/skia/src/codec /home/lonerr/Study/skia/src/core /home/lonerr/Study/skia/src/effects /home/lonerr/Study/skia/src/fonts /home/lonerr/Study/skia/src/image /home/lonerr/Study/skia/src/images /home/lonerr/Study/skia/src/lazy /home/lonerr/Study/skia/src/opts /home/lonerr/Study/skia/src/pathops /home/lonerr/Study/skia/src/pdf /home/lonerr/Study/skia/src/ports /home/lonerr/Study/skia/src/sfnt /home/lonerr/Study/skia/src/shaders /home/lonerr/Study/skia/src/shaders/gradients /home/lonerr/Study/skia/src/sksl /home/lonerr/Study/skia/src/utils /home/lonerr/Study/skia/src/utils/win /home/lonerr/Study/skia/src/xml /home/lonerr/Study/skia/third_party/gif /home/lonerr/Study/skia/src/gpu /home/lonerr/Study/skia/tools/gpu/vk /home/lonerr/Study/skia/include/android /home/lonerr/Study/skia/include/c /home/lonerr/Study/skia/include/codec /home/lonerr/Study/skia/include/config /home/lonerr/Study/skia/include/core /home/lonerr/Study/skia/include/docs /home/lonerr/Study/skia/include/effects /home/lonerr/Study/skia/include/encode /home/lonerr/Study/skia/include/gpu /home/lonerr/Study/skia/include/atlastext /home/lonerr/Study/skia/include/pathops /home/lonerr/Study/skia/include/ports /home/lonerr/Study/skia/include/svg /home/lonerr/Study/skia/include/utils /home/lonerr/Study/skia/include/utils/mac /home/lonerr/Study/skia/include/atlastext)

add_library(gpu_tool_utils SHARED ${src})