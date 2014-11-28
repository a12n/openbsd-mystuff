# $OpenBSD: $

VSN = 1.0devel
COMMENT = fully featured game engine

CATEGORIES = devel games

HOMEPAGE = http://www.godotengine.org/

# MIT
PERMIT_PACKAGE_CDROM = Yes

GH_ACCOUNT = okamstudio
GH_PROJECT = godot
GH_COMMIT = e709468bb13e795cff72b3e87198c61c5b1a2ee7

DISTNAME = ${GH_PROJECT}-${VSN}

WANTLIB += GL GLU X11 Xau Xcursor Xdmcp Xfixes Xrender ao c
WANTLIB += crypto freetype m pthread pthread-stubs ssl stdc++ xcb z

MODULES = devel/scons
LIB_DEPENDS = audio/libao

MODSCONS_FLAGS = ao=yes platform=x11 target=release_debug

do-install:
	${INSTALL_PROGRAM} ${WRKBUILD}/bin/godot.x11.opt.tools.64 ${PREFIX}/bin/godot

.include <bsd.port.mk>
