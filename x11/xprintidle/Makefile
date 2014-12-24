# $OpenBSD: $

VSN =		0.2.1
COMMENT =	utility to query X server for the user\'s idle time

CATEGORIES =		x11

# GPLv2
PERMIT_PACKAGE_CDROM =	Yes

GH_ACCOUNT =		rleitner
GH_PROJECT =		xprintidle
GH_TAGNAME =		0.2.1
GH_COMMIT =		2e0c4fbd296baeeed76d0b9e27ad991ffe8c9613

HOMEPAGE =		https://github.com/${GH_ACCOUNT}/${GH_PROJECT}

DISTNAME =	${GH_PROJECT}-${VSN}

WANTLIB += X11 Xext Xss c

CONFIGURE_STYLE =	gnu
CONFIGURE_ENV =		CPPFLAGS="-I${LOCALBASE}/include \
				-I${X11BASE}/include" \
			LDFLAGS="-L${LOCALBASE}/lib \
				-L${X11BASE}/lib"

.include <bsd.port.mk>
