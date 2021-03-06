project(libstagefright)

set(STAGEFRIGHT_ROOT ${ANDROID_ROOT}/frameworks/av/media/libstagefright)

set(SOURCE_FILES
        ${STAGEFRIGHT_ROOT}/ACodec.cpp
        ${STAGEFRIGHT_ROOT}/ACodecBufferChannel.cpp
        ${STAGEFRIGHT_ROOT}/AACExtractor.cpp
        ${STAGEFRIGHT_ROOT}/AACWriter.cpp
        ${STAGEFRIGHT_ROOT}/AMRExtractor.cpp
        ${STAGEFRIGHT_ROOT}/AMRWriter.cpp
        ${STAGEFRIGHT_ROOT}/AudioPlayer.cpp
        ${STAGEFRIGHT_ROOT}/AudioSource.cpp
        ${STAGEFRIGHT_ROOT}/BufferImpl.cpp
        ${STAGEFRIGHT_ROOT}/CodecBase.cpp
        ${STAGEFRIGHT_ROOT}/CallbackDataSource.cpp
        ${STAGEFRIGHT_ROOT}/CameraSource.cpp
        ${STAGEFRIGHT_ROOT}/CameraSourceTimeLapse.cpp
        ${STAGEFRIGHT_ROOT}/DataConverter.cpp
        ${STAGEFRIGHT_ROOT}/DataSource.cpp
        ${STAGEFRIGHT_ROOT}/DataURISource.cpp
        ${STAGEFRIGHT_ROOT}/ESDS.cpp
        ${STAGEFRIGHT_ROOT}/FileSource.cpp
        ${STAGEFRIGHT_ROOT}/FLACExtractor.cpp
        ${STAGEFRIGHT_ROOT}/FrameRenderTracker.cpp
        ${STAGEFRIGHT_ROOT}/HTTPBase.cpp
        ${STAGEFRIGHT_ROOT}/HevcUtils.cpp
        ${STAGEFRIGHT_ROOT}/ItemTable.cpp
        ${STAGEFRIGHT_ROOT}/JPEGSource.cpp
        ${STAGEFRIGHT_ROOT}/MP3Extractor.cpp
        ${STAGEFRIGHT_ROOT}/MPEG2TSWriter.cpp
        ${STAGEFRIGHT_ROOT}/MPEG4Extractor.cpp
        ${STAGEFRIGHT_ROOT}/MPEG4Writer.cpp
        ${STAGEFRIGHT_ROOT}/MediaAdapter.cpp
        ${STAGEFRIGHT_ROOT}/MediaClock.cpp
        ${STAGEFRIGHT_ROOT}/MediaCodec.cpp
        ${STAGEFRIGHT_ROOT}/MediaCodecList.cpp
        ${STAGEFRIGHT_ROOT}/MediaCodecListOverrides.cpp
        ${STAGEFRIGHT_ROOT}/MediaCodecSource.cpp
        ${STAGEFRIGHT_ROOT}/MediaExtractor.cpp
        ${STAGEFRIGHT_ROOT}/MediaSync.cpp
        ${STAGEFRIGHT_ROOT}/MidiExtractor.cpp
        ${STAGEFRIGHT_ROOT}/http/MediaHTTP.cpp
        ${STAGEFRIGHT_ROOT}/MediaMuxer.cpp
        ${STAGEFRIGHT_ROOT}/MediaSource.cpp
        ${STAGEFRIGHT_ROOT}/NuCachedSource2.cpp
        ${STAGEFRIGHT_ROOT}/NuMediaExtractor.cpp
        ${STAGEFRIGHT_ROOT}/OMXClient.cpp
        ${STAGEFRIGHT_ROOT}/OmxInfoBuilder.cpp
        ${STAGEFRIGHT_ROOT}/OggExtractor.cpp
        ${STAGEFRIGHT_ROOT}/SampleIterator.cpp
        ${STAGEFRIGHT_ROOT}/SampleTable.cpp
        ${STAGEFRIGHT_ROOT}/SimpleDecodingSource.cpp
        ${STAGEFRIGHT_ROOT}/SkipCutBuffer.cpp
        ${STAGEFRIGHT_ROOT}/StagefrightMediaScanner.cpp
        ${STAGEFRIGHT_ROOT}/StagefrightMetadataRetriever.cpp
        ${STAGEFRIGHT_ROOT}/SurfaceMediaSource.cpp
        ${STAGEFRIGHT_ROOT}/SurfaceUtils.cpp
        ${STAGEFRIGHT_ROOT}/ThrottledSource.cpp
        ${STAGEFRIGHT_ROOT}/Utils.cpp
        ${STAGEFRIGHT_ROOT}/VBRISeeker.cpp
        ${STAGEFRIGHT_ROOT}/VideoFrameScheduler.cpp
        ${STAGEFRIGHT_ROOT}/WAVExtractor.cpp
        ${STAGEFRIGHT_ROOT}/XINGSeeker.cpp
        ${STAGEFRIGHT_ROOT}/avc_utils.cpp
        )

include_directories(${STAGEFRIGHT_ROOT})
include_directories(${ANDROID_ROOT}/frameworks/av/include)
include_directories(${ANDROID_ROOT}/frameworks/native/include)



add_library(libstagefright SHARED ${SOURCE_FILES})
target_include_directories(libstagefright PUBLIC
        ${STAGEFRIGHT_ROOT}/include
        ${ANDROID_ROOT}/frameworks/av/media/libmedia/include
        ${ANDROID_ROOT}/frameworks/av/media/libmedia/aidl
        ${INTERMEDIATES_ROOT}/frameworks/av/media/libmedia/libmedia/android_arm64_armv8-a_cortex-a53_shared_core/gen/aidl
        ${ANDROID_ROOT}/system/libhidl/libhidlmemory/include
        ${ANDROID_ROOT}/system/libhidl/transport/memory/1.0/default
        ${ANDROID_ROOT}/system/libhidl/transport/token/1.0/utils/include
        ${INTERMEDIATES_ROOT}/hardware/interfaces/media/omx/1.0/android.hardware.media.omx@1.0_genc++_headers/gen
        ${INTERMEDIATES_ROOT}/hardware/interfaces/media/1.0/android.hardware.media@1.0_genc++_headers/gen
        ${INTERMEDIATES_ROOT}/hardware/interfaces/graphics/common/1.0/android.hardware.graphics.common@1.0_genc++_headers/gen
        ${INTERMEDIATES_ROOT}/hardware/interfaces/graphics/bufferqueue/1.0/android.hardware.graphics.bufferqueue@1.0_genc++_headers/gen
        ${ANDROID_ROOT}/frameworks/av/media/libstagefright/foundation/include
        ${INTERMEDIATES_ROOT}/system/libhidl/transport/memory/1.0/android.hidl.memory@1.0_genc++_headers/gen
        ${ANDROID_ROOT}/external/icu/icu4c/source/i18n
        ${ANDROID_ROOT}/external/icu/icu4c/source/common
        ${ANDROID_ROOT}/external/sonivox/arm-wt-22k/include
        ${INTERMEDIATES_ROOT}/system/libhidl/transport/allocator/1.0/android.hidl.allocator@1.0_genc++_headers/gen
        )
target_compile_definitions(libstagefright PRIVATE
        -DENABLE_STAGEFRIGHT_EXPERIMENTS
        )
target_compile_options(libstagefright PRIVATE
        -Wno-multichar
        -Werror
        -Wno-error=deprecated-declarations
        -Wall
        -fsanitize=unsigned-integer-overflow,signed-integer-overflow
        -fsanitize-trap=all
        -ftrap-function=abort
        )
target_link_libraries(libstagefright
        libaudioutils
        libbinder
        libcamera_client
        libcrypto
        libcutils
        libdrmframework
        libexpat
        libgui
        liblog
        libmedia
        libaudioclient
        libmediametrics
        libmediautils
        libnetd_client
        libsonivox
        libui
        libutils
        libvorbisidec
        libmediadrm
        libnativewindow

        libmedia_helper
        libstagefright_omx_utils
        libstagefright_flacdec
        libstagefright_foundation
        libstagefright_xmlparser
        libRScpp
        libhidlbase
        libhidlmemory

        libstagefright_color_conversion
        libyuv_static
        libstagefright_aacenc
        libstagefright_matroska
        libstagefright_mediafilter
        libstagefright_webm
        libstagefright_timedtext
        libvpx
        libwebm
        libstagefright_mpeg2ts
        libstagefright_id3
        libFLAC

        android.hidl.memory-1.0
        android.hidl.token-1.0-utils
        android.hidl.allocator-1.0
        android.hardware.cas-1.0
        android.hardware.cas.native-1.0
        android.hardware.media.omx-1.0
        )