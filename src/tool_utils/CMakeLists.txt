cmake_minimum_required(VERSION 3.3)

project(tool_utils)

set(src AndroidSkDebugToStdOut.cpp CrashHandler.cpp DDLPromiseImageHelper.cpp DDLTileHelper.cpp LsanSuppressions.cpp ProcStats.cpp Resources.cpp UrlDataManager.cpp debugger/SkDebugCanvas.cpp debugger/SkDrawCommand.cpp debugger/SkJsonWriteBuffer.cpp fonts/SkRandomScalerContext.cpp fonts/SkTestEmptyTypeface.h fonts/SkTestFontMgr.cpp fonts/SkTestFontMgr.h fonts/SkTestSVGTypeface.cpp fonts/SkTestSVGTypeface.h fonts/SkTestTypeface.cpp fonts/SkTestTypeface.h fonts/sk_tool_utils_font.cpp random_parse_path.cpp sk_tool_utils.cpp timer/SkAnimTimer.h timer/Timer.cpp trace/SkChromeTracingTracer.cpp trace/SkChromeTracingTracer.h trace/SkDebugfTracer.cpp trace/SkDebugfTracer.h trace/SkEventTracingPriv.cpp trace/SkEventTracingPriv.h)

set(lib)

if(DEFINED is_ios)
    set(src ${src} ios_utils.m)
    set(lib ${lib} Foundation.framework)
endif()

include_directories(/home/lonerr/Study/skia/tools /home/lonerr/Study/skia/tools/debugger /home/lonerr/Study/skia/tools/fonts /home/lonerr/Study/skia/tools/timer /home/lonerr/Study/skia/tools/trace /home/lonerr/Study/skia/include/private /home/lonerr/Study/skia/src/c /home/lonerr/Study/skia/src/codec /home/lonerr/Study/skia/src/core /home/lonerr/Study/skia/src/effects /home/lonerr/Study/skia/src/fonts /home/lonerr/Study/skia/src/image /home/lonerr/Study/skia/src/images /home/lonerr/Study/skia/src/lazy /home/lonerr/Study/skia/src/opts /home/lonerr/Study/skia/src/pathops /home/lonerr/Study/skia/src/pdf /home/lonerr/Study/skia/src/ports /home/lonerr/Study/skia/src/sfnt /home/lonerr/Study/skia/src/shaders /home/lonerr/Study/skia/src/shaders/gradients /home/lonerr/Study/skia/src/sksl /home/lonerr/Study/skia/src/utils /home/lonerr/Study/skia/src/utils/win /home/lonerr/Study/skia/src/xml /home/lonerr/Study/skia/third_party/gif /home/lonerr/Study/skia/src/gpu /home/lonerr/Study/skia/tools/gpu/vk /home/lonerr/Study/skia/tools/flags /home/lonerr/Study/skia/tools/gpu /home/lonerr/Study/skia/third_party/vulkan /home/lonerr/Study/skia/experimental/svg/model /home/lonerr/Study/skia/tools/flags /home/lonerr/Study/skia/include/android /home/lonerr/Study/skia/include/c /home/lonerr/Study/skia/include/codec /home/lonerr/Study/skia/include/config /home/lonerr/Study/skia/include/core /home/lonerr/Study/skia/include/docs /home/lonerr/Study/skia/include/effects /home/lonerr/Study/skia/include/encode /home/lonerr/Study/skia/include/gpu /home/lonerr/Study/skia/include/atlastext /home/lonerr/Study/skia/include/pathops /home/lonerr/Study/skia/include/ports /home/lonerr/Study/skia/include/svg /home/lonerr/Study/skia/include/utils /home/lonerr/Study/skia/include/utils/mac /home/lonerr/Study/skia/include/atlastext /home/lonerr/Study/skia/third_party/externals/jsoncpp/include /home/lonerr/Study/skia/third_party/libpng /home/lonerr/Study/skia/third_party/externals/libpng)

add_library(tool_utils SHARED ${src})