SUBDIRS = pixmaps\
		  icons\
		  ${PLUGINS_DIRS}\
		  po\
		  intl

bin_PROGRAMS = deadbeef

INTLTOOL_FILES = \
		intltool-extract.in \
		intltool-merge.in \
		intltool-update.in

DISTCLEANFILES = \
		intltool-extract \
		intltool-merge \
		intltool-update

deadbeef_SOURCES =\
	main.c common.h deadbeef.h\
	plugins.c plugins.h moduleconf.h\
	shared/cueutil.c shared/cueutil.h playlist.c playlist.h \
	plmeta.c pltmeta.c pltmeta.h\
	streamer.c streamer.h\
	dsp.c dsp.h\
	streamreader.c streamreader.h\
	premix.c premix.h\
	messagepump.c messagepump.h\
	conf.c  conf.h\
	threading_pthread.c threading.h\
	volume.c volume.h\
	junklib.h junklib.c utf8.c utf8.h\
	u8_lc_map.h\
	u8_uc_map.h\
	fastftoi.h\
	vfs.c vfs.h vfs_stdio.c\
	md5/md5.c md5/md5.h\
	metacache.c metacache.h\
	gettext.h\
	ringbuf.c ringbuf.h\
	dsppreset.c dsppreset.h\
	replaygain.c replaygain.h\
	fft.c fft.h\
	handler.c handler.h\
	strdupa.h\
	escape.c escape.h\
	tf.c tf.h\
	playqueue.c playqueue.h\
	sort.c sort.h\
	logger.c logger.h
	
#	ConvertUTF/ConvertUTF.c ConvertUTF/ConvertUTF.h

sdkdir = $(pkgincludedir)
sdk_HEADERS = deadbeef.h

deadbeef_LDADD = $(LDADD) $(DEPS_LIBS) $(ICONV_LIB) $(DL_LIBS) -lm -lpthread $(INTL_LIBS) plugins/libparser/libparser.a

AM_CFLAGS = $(DEPS_CFLAGS) -std=c99
AM_CPPFLAGS = $(DEPS_CFLAGS)

docsdir = $(docdir)

docs_DATA = README help.txt about.txt translators.txt ChangeLog\
	COPYING.GPLv2 COPYING.LGPLv2.1\
	translation/help.ru.txt\
	translation/help.pt_BR.txt

desktopdir = $(datadir)/applications
desktop_DATA = deadbeef.desktop

EXTRA_DIST = $(docs_DATA) $(desktop_DATA) $(INTLTOOL_FILES) translation/extra.c sj_to_unicode.h examples/decoder_template.c examples/dsp_template.c yasmwrapper.sh

ACLOCAL_AMFLAGS = -I m4
