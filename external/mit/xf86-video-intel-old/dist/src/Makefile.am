#  Copyright 2005 Adam Jackson.
#
#  Permission is hereby granted, free of charge, to any person obtaining a
#  copy of this software and associated documentation files (the "Software"),
#  to deal in the Software without restriction, including without limitation
#  on the rights to use, copy, modify, merge, publish, distribute, sub
#  license, and/or sell copies of the Software, and to permit persons to whom
#  the Software is furnished to do so, subject to the following conditions:
#
#  The above copyright notice and this permission notice (including the next
#  paragraph) shall be included in all copies or substantial portions of the
#  Software.
#
#  THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
#  IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
#  FITNESS FOR A PARTICULAR PURPOSE AND NON-INFRINGEMENT.  IN NO EVENT SHALL
#  ADAM JACKSON BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER
#  IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN
#  CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.

SUBDIRS = xvmc bios_reader ch7017 ch7xxx ivch sil164 tfp410 reg_dumper render_program

# this is obnoxious:
# -module lets us name the module exactly how we want
# -avoid-version prevents gratuitous .0.0.0 version numbers on the end
# _ladir passes a dummy rpath to libtool so the thing will actually link
# TODO: -nostdlib/-Bstatic/-lgcc platform magic, not installing the .a, etc.

AM_CFLAGS = @WARN_CFLAGS@ @XORG_CFLAGS@ @DRM_CFLAGS@ @DRI_CFLAGS@ \
	@PCIACCESS_CFLAGS@ -I$(top_srcdir)/uxa -I$(top_srcdir)/src/render_program

intel_drv_la_LTLIBRARIES = intel_drv.la
intel_drv_la_LDFLAGS = -module -avoid-version
intel_drv_ladir = @moduledir@/drivers
intel_drv_la_LIBADD = -lm @DRM_LIBS@ -ldrm_intel ../uxa/libuxa.la
intel_drv_la_LIBADD += @PCIACCESS_LIBS@

INTEL_DRI_SRCS = \
         i810_dri.c \
         i810_dri.h \
         i830_dri.c \
         i810_hwmc.c \
         i830_dri.h

INTEL_XVMC_SRCS = \
	 i830_hwmc.h \
	 i830_hwmc.c \
         i915_hwmc.c \
         i915_hwmc.h \
         i965_hwmc.c \
         i965_hwmc.h


intel_drv_la_SOURCES = \
         brw_defines.h \
         brw_structs.h \
         common.h \
	 i2c_vid.h \
         i810_accel.c \
         i810_common.h \
         i810_cursor.c \
         i810_dga.c \
         i810_driver.c \
         i810.h \
         i810_io.c \
         i810_memory.c \
         i810_reg.h \
         i810_ring.h \
         i810_video.c \
         i810_wmark.c \
	 i830_3d.c \
         i830_accel.c \
         i830_bios.c \
         i830_bios.h \
         i830_batchbuffer.c \
         i830_batchbuffer.h \
         i830_common.h \
	 i830_crt.c \
         i830_cursor.c \
	 i830_debug.c \
	 i830_debug.h \
	 i830_display.c \
	 i830_display.h \
         i830_quirks.c \
         i830_driver.c \
	 i830_dvo.c \
         i830.h \
	 i830_hdmi.c \
         i830_i2c.c \
         i830_io.c \
	 i830_lvds.c \
         i830_memory.c \
         i830_modes.c \
         i830_video.c \
         i830_video.h \
	 i830_reg.h \
         i830_ring.h \
	 i830_sdvo.c \
	 i830_sdvo.h \
	 i830_sdvo_regs.h \
	 i830_tv.c \
	 i915_3d.c \
	 i915_3d.h \
	 i915_reg.h \
	 i915_video.c \
	 i965_video.c \
	 i830_uxa.c \
	 i830_render.c \
	 i915_render.c \
	 i965_render.c \
	 drmmode_display.c

EXTRA_DIST = 		\
	$(XMODE_SRCS)	\
	$(INTEL_DRI_SRCS) \
	$(INTEL_XVMC_SRCS)

if DRI
intel_drv_la_SOURCES += \
	$(INTEL_DRI_SRCS)
intel_drv_la_LIBADD += \
	$(DRI_LIBS)
endif

if XVMC
intel_drv_la_SOURCES += \
	$(INTEL_XVMC_SRCS)
endif
