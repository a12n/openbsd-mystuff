# $OpenBSD: Makefile,v 1.9 2015/07/18 14:33:49 jasper Exp $

COMMENT =	ncurses-based music player

CATEGORIES =	audio

HOMEPAGE =	https://cmus.github.io/

# GPLv2+
PERMIT_PACKAGE_CDROM =	Yes

V =	2.7.1
GH_ACCOUNT =	cmus
GH_PROJECT =	cmus
GH_TAGNAME =	v${V}

DISTNAME =	${GH_PROJECT}-v${V}
PKGNAME =	${GH_PROJECT}-${V}

SHARED_ONLY =	Yes

MODULES =	converters/libiconv

WANTLIB =	FLAC>=5 c cdio cdio_cdda cue faad m mad>=2 modplug mpcdec
WANTLIB +=	ncursesw opusfile pthread sndio wavpack
WANTLIB +=	${MODLIBICONV_WANTLIB}

LIB_DEPENDS = 	audio/faad audio/flac audio/libcdio audio/libcue
LIB_DEPENDS +=	audio/libmad audio/libmodplug audio/musepack
LIB_DEPENDS +=	audio/opusfile audio/wavpack ${MODLIBICONV_LIB_DEPENDS}

USE_GMAKE =	Yes

CONFIGURE_STYLE =	simple
CONFIGURE_ENV =		HOSTCC="${CC}" HOSTLD="${CC}" HOST_CFLAGS="${CFLAGS}"
# Note: We're explicitly disabling CONFIG_CDDB as it gets undef'd in cdio.c
CONFIGURE_ARGS =	prefix=${PREFIX} \
			exampledir=${PREFIX}/share/examples/cmus \
			mandir=${PREFIX}/man \
			CONFIG_AAC=y \
			CONFIG_ALSA=n \
			CONFIG_AO=n \
			CONFIG_ARTS=n \
			CONFIG_CDDB=n \
			CONFIG_CDIO=y \
			CONFIG_CUE=y \
			CONFIG_DISCID=n \
			CONFIG_FFMPEG=n \
			CONFIG_FLAC=y \
			CONFIG_JACK=n \
			CONFIG_MAD=y \
			CONFIG_MODPLUG=y \
			CONFIG_MP4=n \
			CONFIG_MPC=y \
			CONFIG_OPUS=y \
			CONFIG_OSS=n \
			CONFIG_PULSE=n \
			CONFIG_ROAR=n \
			CONFIG_SAMPLERATE=n \
			CONFIG_SNDIO=y \
			CONFIG_SUN=n \
			CONFIG_VORBIS=y \
			CONFIG_VTX=n \
			CONFIG_WAVPACK=y

.if ${MACHINE_ARCH} == "arm"
CONFIGURE_ARGS +=	CONFIG_TREMOR=y
LIB_DEPENDS +=	audio/tremor
WANTLIB +=		vorbisidec>=1
.else
LIB_DEPENDS +=	audio/libvorbis
# WANTLIB +=		ogg vorbis>=0 vorbisfile>=1
WANTLIB +=		vorbisfile>=1
.endif

NO_TEST =	Yes

post-patch:
	sed -i s,/usr,${LOCALBASE}, ${WRKSRC}/Doc/cmus.txt
	sed -i s,doc/cmus/examples,examples/cmus, ${WRKSRC}/Doc/cmus.txt

.include <bsd.port.mk>
