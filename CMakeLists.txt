cmake_minimum_required(VERSION 3.4.1)

project(baresip)

set(CMAKE_C_FLAGS "${CMAKE_C_FLAGS} -g -ggdb")
set(CMAKE_C_FLAGS "${CMAKE_C_FLAGS} -DHAVE_INTTYPES_H")
set(CMAKE_C_FLAGS "${CMAKE_C_FLAGS} -DHAVE_INET6")
set(CMAKE_C_FLAGS "${CMAKE_C_FLAGS} -DUSE_X264")
set(CMAKE_C_FLAGS "${CMAKE_C_FLAGS} -DHAVE_INET6")
set(CMAKE_C_FLAGS "${CMAKE_C_FLAGS} -DUSE_VIDEO=1")
set(CMAKE_C_FLAGS "${CMAKE_C_FLAGS} -DSTATIC=1")
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -DSTATIC=1")
set(CMAKE_C_FLAGS "${CMAKE_C_FLAGS} -DCONFIG_PATH='\"/data/data/com.xyt.sipphone\"'")

set(source_list
    ../../src/main/cpp/baresip/src/main.c
    ../../src/main/cpp/baresip/src/static.c
    ../../src/main/cpp/baresip/src/account.c
    ../../src/main/cpp/baresip/src/aucodec.c
    ../../src/main/cpp/baresip/src/audio.c
    ../../src/main/cpp/baresip/src/aufilt.c
    ../../src/main/cpp/baresip/src/aulevel.c
    ../../src/main/cpp/baresip/src/auplay.c
    ../../src/main/cpp/baresip/src/ausrc.c
    ../../src/main/cpp/baresip/src/baresip.c
    ../../src/main/cpp/baresip/src/call.c
    ../../src/main/cpp/baresip/src/cmd.c
    ../../src/main/cpp/baresip/src/conf.c
    ../../src/main/cpp/baresip/src/config.c
    ../../src/main/cpp/baresip/src/contact.c
    ../../src/main/cpp/baresip/src/log.c
    ../../src/main/cpp/baresip/src/menc.c
    ../../src/main/cpp/baresip/src/message.c
    ../../src/main/cpp/baresip/src/metric.c
    ../../src/main/cpp/baresip/src/mnat.c
    ../../src/main/cpp/baresip/src/module.c
    ../../src/main/cpp/baresip/src/mos.c
    ../../src/main/cpp/baresip/src/net.c
    ../../src/main/cpp/baresip/src/play.c
    ../../src/main/cpp/baresip/src/realtime.c
    ../../src/main/cpp/baresip/src/reg.c
    ../../src/main/cpp/baresip/src/rtpext.c
    ../../src/main/cpp/baresip/src/rtpkeep.c
    ../../src/main/cpp/baresip/src/sdp.c
    ../../src/main/cpp/baresip/src/sipreq.c
    ../../src/main/cpp/baresip/src/stream.c
    ../../src/main/cpp/baresip/src/ua.c
    ../../src/main/cpp/baresip/src/ui.c
    ../../src/main/cpp/baresip/src/bfcp.c
    ../../src/main/cpp/baresip/src/h264.c
    ../../src/main/cpp/baresip/src/mctrl.c
    ../../src/main/cpp/baresip/src/video.c
    ../../src/main/cpp/baresip/src/vidcodec.c
    ../../src/main/cpp/baresip/src/vidfilt.c
    ../../src/main/cpp/baresip/src/vidisp.c
    ../../src/main/cpp/baresip/src/vidsrc.c
    ../../src/main/cpp/baresip/src/vidutil.c

    ../../src/main/cpp/baresip/modules/jdkcodec/decode.c
    ../../src/main/cpp/baresip/modules/jdkcodec/encode.c
    ../../src/main/cpp/baresip/modules/jdkcodec/sdp.c
    ../../src/main/cpp/baresip/modules/jdkcodec/h264.c

    ../../src/main/cpp/baresip/modules/androidgles/opengles.c
    ../../src/main/cpp/baresip/modules/androidgles/context.c

    ../../src/main/cpp/baresip/modules/g711/g711.c
    ../../src/main/cpp/baresip/modules/opensles/opensles.c
    ../../src/main/cpp/baresip/modules/opensles/player.c
    ../../src/main/cpp/baresip/modules/opensles/recorder.c

    ../../src/main/cpp/baresip/modules/syslog/syslog.c
    ../../src/main/cpp/baresip/modules/contact/contact.c
    ../../src/main/cpp/baresip/modules/menu/menu.c
    ../../src/main/cpp/baresip/modules/account/account.c
    ../../src/main/cpp/baresip/modules/uuid/uuid.c
    ../../src/main/cpp/baresip/modules/fakevideo/fakevideo.c
)

include_directories(../../src/main/cpp/vpx/include)
include_directories(../../src/main/cpp/re/include)
include_directories(../../src/main/cpp/rem/include)
include_directories(../../src/main/cpp/baresip/include)
add_library(baresip STATIC ${source_list})

target_link_libraries(baresip "re")
target_link_libraries(baresip "rem")
target_link_libraries(baresip "vpx")
#target_link_libraries(baresip "${PROJECT_SOURCE_DIR}/../../src/main/cpp/libopenh264/lib/libopenh264.so")

target_link_libraries(baresip EGL GLESv1_CM android OpenSLES)
