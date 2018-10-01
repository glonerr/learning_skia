cmake_minimum_required(VERSION 3.3)

project(sk_app)

set(src CommandSet.cpp GLWindowContext.cpp Window.cpp)

set(lib)

if(DEFINED is_android)
    set(src ${src} android/GLWindowContext_android.cpp android/RasterWindowContext_android.cpp android/Window_android.cpp android/main_android.cpp android/surface_glue_android.cpp)
    set(lib ${lib} android)
elseif(DEFINED is_linux)
    set(src ${src} unix/GLWindowContext_unix.cpp unix/RasterWindowContext_unix.cpp unix/Window_unix.cpp unix/keysym2ucs.c unix/main_unix.cpp)
    set(lib ${lib} GLU X11)
elseif(DEFINED is_win)
    set(src ${src} win/GLWindowContext_win.cpp win/RasterWindowContext_win.cpp win/Window_win.cpp win/main_win.cpp)
    if (DEFINED skia_use_angle)
        set(src ${src} win/ANGLEWindowContext_win.cpp)
    endif()
elseif(DEFINED is_mac)
    set(src ${src} mac/GLWindowContext_mac.cpp  mac/RasterWindowContext_mac.cpp  mac/Window_mac.cpp  mac/main_mac.cpp)
    set(lib ${lib} QuartzCore.framework Cocoa.framework Foundation.framework)
elseif(DEFINED is_ios)
    set(src ${src} ios/GLWindowContext_ios.cpp ios/RasterWindowContext_ios.cpp ios/Window_ios.cpp ios/main_ios.cpp)
endif()

if(DEFINED skia_use_vulkan)
    set(src ${src} VulkanWindowContext.cpp)
    if(is_android)
        set(src ${src} android/VulkanWindowContext_android.cpp)
    elseif(is_linux)
        set(src ${src} unix/VulkanWindowContext_unix.cpp)
        set(lib ${lib} X11-xcb)
    elseif(is_win)
        set(src ${src} win/VulkanWindowContext_win.cpp)
    endif()
endif()

include_directories(/home/lonerr/Study/skia/tools/sk_app /home/lonerr/Study/skia/include/private /home/lonerr/Study/skia/src/c /home/lonerr/Study/skia/src/codec /home/lonerr/Study/skia/src/core /home/lonerr/Study/skia/src/effects /home/lonerr/Study/skia/src/fonts /home/lonerr/Study/skia/src/image /home/lonerr/Study/skia/src/images /home/lonerr/Study/skia/src/lazy /home/lonerr/Study/skia/src/opts /home/lonerr/Study/skia/src/pathops /home/lonerr/Study/skia/src/pdf /home/lonerr/Study/skia/src/ports /home/lonerr/Study/skia/src/sfnt /home/lonerr/Study/skia/src/shaders /home/lonerr/Study/skia/src/shaders/gradients /home/lonerr/Study/skia/src/sksl /home/lonerr/Study/skia/src/utils /home/lonerr/Study/skia/src/utils/win /home/lonerr/Study/skia/src/xml /home/lonerr/Study/skia/third_party/gif /home/lonerr/Study/skia/src/gpu /home/lonerr/Study/skia/tools/gpu/vk /home/lonerr/Study/skia/tools/gpu /home/lonerr/Study/skia/third_party/vulkan /home/lonerr/Study/skia/include/android /home/lonerr/Study/skia/include/c /home/lonerr/Study/skia/include/codec /home/lonerr/Study/skia/include/config /home/lonerr/Study/skia/include/core /home/lonerr/Study/skia/include/docs /home/lonerr/Study/skia/include/effects /home/lonerr/Study/skia/include/encode /home/lonerr/Study/skia/include/gpu /home/lonerr/Study/skia/include/atlastext /home/lonerr/Study/skia/include/pathops /home/lonerr/Study/skia/include/ports /home/lonerr/Study/skia/include/svg /home/lonerr/Study/skia/include/utils /home/lonerr/Study/skia/include/utils/mac /home/lonerr/Study/skia/include/atlastext /home/lonerr/Study/skia/tools /home/lonerr/Study/skia/tools/debugger /home/lonerr/Study/skia/tools/fonts /home/lonerr/Study/skia/tools/timer /home/lonerr/Study/skia/tools/trace /home/lonerr/Study/skia/tools/flags)

add_library(sk_app SHARED ${src})

target_link_libraries(sk_app /home/lonerr/Documents/workspace/vscode/skia/libs/libskia.a tool_utils)