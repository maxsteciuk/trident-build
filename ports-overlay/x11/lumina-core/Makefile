# $FreeBSD$

PORTNAME=	lumina-core
PORTVERSION=	1.4.2
PORTREVISION=	201811161500
CATEGORIES=	x11

MAINTAINER=	jt@ixsystems.com
COMMENT=	Lumina Desktop Environment

LICENSE=	BSD3CLAUSE

RUN_DEPENDS=	fluxbox>=0:x11-wm/fluxbox \
		xscreensaver>=0:x11/xscreensaver \
		xbrightness>=0:x11/xbrightness \
		compton>=0:x11-wm/compton \
		xrandr>=0:x11/xrandr \
		numlockx>=0:x11/numlockx
LIB_DEPENDS+=	libxcb-ewmh.so:x11/xcb-util-wm \
		libxcb-icccm.so:x11/xcb-util-wm \
		libxcb-image.so:x11/xcb-util-image \
		libxcb-util.so:x11/xcb-util \
		libXcursor.so:x11/libXcursor

CONFLICTS_INSTALL=	lumina-1.2.*

OPTIONS_DEFINE=	MULTIMEDIA TRUEOS I18N
OPTIONS_SUB=		yes
OPTIONS_DEFAULT=	MULTIMEDIA I18N
MULTIMEDIA_DESC=	Install multimedia support backend (gstreamer)
TRUEOS_DESC=	Use the TrueOS system interface settings.
I18N_DESC= Install localization files

.include <bsd.port.options.mk>

.if ${PORT_OPTIONS:MMULTIMEDIA}
RUN_DEPENDS+=	gstreamer1-plugins-core>=0:multimedia/gstreamer1-plugins-core
.endif

MAKE_JOBS_UNSAFE=yes
USES=		qmake qt:5

USE_GL=		gl
USE_XORG=	x11 xdamage xcb
USE_LDCONFIG=	yes
USE_QT=		core gui widgets network svg multimedia imageformats \
		buildtools_build x11extras concurrent

USE_GITHUB=	yes
GH_ACCOUNT=	trueos
GH_PROJECT=	lumina
GH_TAGNAME=	55cef5db77196940eb0a55e71f6f182869469fa8
WRKSRC_SUBDIR=	src-qt5/core

#Setup the qmake configuration options
.if ${PORT_OPTIONS:MTRUEOS}
QMAKE_ARGS=	DEFAULT_SETTINGS=TrueOS
.endif

.if${PORT_OPTIONS:MI18N}
USE_QT+= linguist_build
QMAKE_ARGS+=CONFIG+=WITH_I18N
.endif

.include <bsd.port.mk>
