# $OpenBSD: $

VSN = 20150404
COMMENT = fully featured game engine

CATEGORIES = devel games

HOMEPAGE = http://www.godotengine.org/

# MIT
PERMIT_PACKAGE_CDROM = Yes

GH_ACCOUNT = a12n
GH_PROJECT = godot
GH_COMMIT = 16746f157f83d666079ba3266acec13d35b84c3f

DISTNAME = ${GH_PROJECT}-${VSN}

WANTLIB += GL GLU X11 Xau Xcursor Xdmcp Xfixes Xrender ao c
WANTLIB += crypto freetype m pthread pthread-stubs ssl stdc++ xcb z

MODULES = devel/scons
LIB_DEPENDS = audio/libao

MODSCONS_FLAGS = ao=yes platform=x11 pulseaudio=no target=release_debug

.include <bsd.port.arch.mk>

.for _m in ${MACHINE_ARCH}
.  if !empty(LP64_ARCHS:M${_m})
BITS =	64
.  endif
.endfor
BITS ?=	32

do-install:
	${INSTALL_PROGRAM} ${WRKBUILD}/bin/godot.x11.opt.tools.${BITS}	\
		${PREFIX}/bin/godot
	${INSTALL_DATA_DIR} ${PREFIX}/share/blender/scripts/addons
	cd ${WRKDIST}/tools/export/blender25; tar cf - io_scene_dae | tar xf - -C \
		${PREFIX}/share/blender/scripts/addons/

.include <bsd.port.mk>
