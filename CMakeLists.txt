cmake_minimum_required(VERSION 3.3)

project(learning_skia)

add_definitions(-D_GLIBCXX_DEBUG -DSK_GAMMA_APPLY_TO_A8 -DSK_ENABLE_DISCRETE_GPU -DGR_TEST_UTILS=1 -DSK_ENABLE_SPIRV_VALIDATION -DSK_HAS_HEIF_LIBRARY -DSK_HAS_JPEG_LIBRARY -DSK_SUPPORT_PDF -DSK_PDF_USE_SFNTLY -DSK_HAS_PNG_LIBRARY -DSK_CODEC_DECODES_RAW -DSK_HAS_WEBP_LIBRARY -DSK_XML -DSK_SAMPLES_FOR_X -DSK_SUPPORT_ATLAS_TEXT=1)

set(is_linux true)

add_subdirectory(src)