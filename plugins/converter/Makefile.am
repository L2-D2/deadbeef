convdata = \
	convpresets/AAC_(Nero_FAAC).txt\
	convpresets/FLAC_(compression_level_5).txt\
	convpresets/MP3_CBR_320_Kbps_(Lame).txt\
	convpresets/MP3_VBR_192Kbps_(Lame).txt\
	convpresets/MS_RIFF_WAV.txt\
	convpresets/MusePack.txt\
	convpresets/Ogg_FLAC.txt\
	convpresets/Ogg_Vorbis_(-q_5).txt\
	convpresets/Opus.txt\
	convpresets/TTA.txt\
	convpresets/WavPack.txt\
	convpresets/ALAC.txt\
	convpresets/File_Copy.txt\
	convpresets/File_Move.txt

EXTRA_DIST = $(convdata) converter.glade

if HAVE_CONVERTER

if HAVE_GTK2
if HAVE_GTK3
pkglib_LTLIBRARIES = converter.la converter_gtk2.la converter_gtk3.la
else
pkglib_LTLIBRARIES = converter.la converter_gtk2.la
endif
else
if HAVE_GTK3
pkglib_LTLIBRARIES = converter.la converter_gtk3.la
endif
endif

convdatadir = $(libdir)/deadbeef/convpresets
convdata_DATA = $(convdata)

converter_la_CFLAGS =  $(CFLAGS) -I@top_srcdir@/plugins/libmp4ff -std=c99 -fPIC -DUSE_TAGGING=1
converter_la_SOURCES = converter.c converter.h\
	../../shared/mp4tagutil.c ../../shared/mp4tagutil.h
converter_la_LDFLAGS = -module -avoid-version
converter_la_LIBADD = $(LDADD) ../libmp4ff/libmp4ff.a

if HAVE_GTK2
converter_gtk2_la_SOURCES = convgui.c interface.c support.c callbacks.h converter.h interface.h support.h
converter_gtk2_la_LDFLAGS = -module -avoid-version
if STATICLINK
GTK_ROOT=@top_srcdir@/$(LIB)/gtk-2.12.12/usr

converter_gtk2_la_LIBADD = $(LDADD) -L$(GTK_ROOT)/lib -lgtk-x11-2.0 -lgdk-x11-2.0 -latk-1.0 -lgdk_pixbuf-2.0 -lm -lpangocairo-1.0 -lpango-1.0 -lcairo -lgobject-2.0 -lgmodule-2.0 -ldl -lglib-2.0 -lrt

converter_gtk2_la_CFLAGS = -std=c99 -I $(GTK_ROOT)/include -I $(GTK_ROOT)/lib/gtk-2.0/include -I $(GTK_ROOT)/include/glib-2.0 -I $(GTK_ROOT)/include/gtk-2.0 -I $(GTK_ROOT)/include/cairo -I $(GTK_ROOT)/lib/glib-2.0/include/ -I $(GTK_ROOT)/include/pango-1.0 -I $(GTK_ROOT)/include/atk-1.0 -DULTRA_COMPATIBLE=1
else
converter_gtk2_la_LIBADD = $(LDADD) $(GTK2_DEPS_LIBS)
converter_gtk2_la_CFLAGS = -std=c99 $(GTK2_DEPS_CFLAGS)
endif
endif

if HAVE_GTK3
converter_gtk3_la_SOURCES = convgui.c interface.c support.c callbacks.h converter.h interface.h support.h
converter_gtk3_la_LDFLAGS = -module -avoid-version
converter_gtk3_la_LIBADD = $(LDADD) $(GTK3_DEPS_LIBS)
converter_gtk3_la_CFLAGS = -std=c99 $(GTK3_DEPS_CFLAGS)
endif

endif
