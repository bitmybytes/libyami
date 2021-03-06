INCLUDES = -I$(top_srcdir) \
	-I$(top_srcdir)/interface \
	-I$(top_srcdir)/common \
	-I$(top_srcdir)/vaapi \
	-I$(top_srcdir)/codecparsers \
	$(NULL)

libyami_encoder_source_c = \
	vaapicodedbuffer.cpp \
	vaapiencpicture.cpp \
	vaapiencoder_base.cpp \
	vaapiencoder_host.cpp \
	$(NULL)

if BUILD_H264_ENCODER
libyami_encoder_source_c += vaapiencoder_h264.cpp
endif

if BUILD_JPEG_ENCODER
libyami_encoder_source_c += vaapiencoder_jpeg.cpp
endif

if BUILD_VP8_ENCODER
libyami_encoder_source_c += vaapiencoder_vp8.cpp
endif

if BUILD_H265_ENCODER
libyami_encoder_source_c += vaapiencoder_hevc.cpp
endif

libyami_encoder_source_h = \
	../interface/VideoCommonDefs.h      \
	../interface/VideoEncoderDefs.h      \
	../interface/VideoEncoderInterface.h \
	../interface/VideoEncoderHost.h \
	$(NULL)

libyami_encoder_source_h_priv = \
	vaapicodedbuffer.h \
	vaapiencpicture.h \
	vaapiencoder_base.h \
	$(NULL)

if BUILD_H264_ENCODER
libyami_encoder_source_h_priv += vaapiencoder_h264.h
endif

if BUILD_JPEG_ENCODER
libyami_encoder_source_h_priv += vaapiencoder_jpeg.h 
endif

if BUILD_VP8_ENCODER
libyami_encoder_source_h_priv += vaapiencoder_vp8.h
endif

if BUILD_H265_ENCODER
libyami_encoder_source_h_priv += vaapiencoder_hevc.h
endif

libyami_encoder_la_LIBADD = \
	$(top_builddir)/common/libyami_common.la \
	$(top_builddir)/vaapi/libyami_vaapi.la \
	$(top_builddir)/codecparsers/libyami_codecparser.la \
	$(NULL)

libyami_encoder_ldflags = \
	$(LIBYAMI_LT_LDFLAGS) \
	$(LIBVA_LIBS) \
	$(LIBVA_DRM_LIBS) \
	-ldl \
	$(NULL)

if ENABLE_X11
libyami_encoder_ldflags += $(LIBVA_X11_LIBS) $(X11_LIBS)
endif

libyami_encoder_cppflags = \
	$(LIBVA_CFLAGS) \
	$(LIBVA_DRM_CFLAGS) \
	$(NULL)

if ENABLE_X11
libyami_encoder_cppflags += $(LIBVA_X11_CFLAGS)
endif

lib_LTLIBRARIES                = libyami_encoder.la
libyami_encoderincludedir      = $(includedir)/libyami_encoder
libyami_encoderinclude_HEADERS = $(libyami_encoder_source_h)
noinst_HEADERS                 = $(libyami_encoder_source_h_priv)
libyami_encoder_la_SOURCES     = $(libyami_encoder_source_c)
libyami_encoder_la_LDFLAGS     = $(libyami_encoder_ldflags)
libyami_encoder_la_CPPFLAGS    = $(libyami_encoder_cppflags)

DISTCLEANFILES = \
	Makefile.in
