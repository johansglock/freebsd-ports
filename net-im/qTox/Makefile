# Created by: Yuri Victorovich <yuri@rawbw.com>
# $FreeBSD$

PORTNAME=	qTox
PORTVERSION=	1.2.4
DISTVERSIONPREFIX=	v
CATEGORIES=	net-im net-p2p

MAINTAINER=	yuri@rawbw.com
COMMENT=	Qt 5 based Tox client

LICENSE=	GPLv3

BUILD_DEPENDS=	${LOCALBASE}/include/linux/videodev2.h:${PORTSDIR}/multimedia/v4l_compat
LIB_DEPENDS=	libtoxcore.so:${PORTSDIR}/net-im/tox \
		libopencv_highgui.so:${PORTSDIR}/graphics/opencv \
		libopencv_core.so:${PORTSDIR}/graphics/opencv-core \
		libavcodec.so:${PORTSDIR}/multimedia/ffmpeg \
		libvpx.so:${PORTSDIR}/multimedia/libvpx \
		libfilteraudio.so:${PORTSDIR}/audio/libfilteraudio \
		libsodium.so:${PORTSDIR}/security/libsodium \
		libqrencode.so:${PORTSDIR}/graphics/libqrencode \
		libsqlcipher.so:${PORTSDIR}/databases/sqlcipher

USE_GITHUB=	yes
GH_ACCOUNT=	tux3

SUB_FILES=	pkg-message

USES=		compiler:c++11-lib desktop-file-utils openal:soft qmake gmake
USE_GNOME=	glib20 gtk20 cairo gdkpixbuf2
USE_XORG=	x11 xscrnsaver
USE_QT5=	core gui network xml opengl sql sql-sqlite3_run widgets svg \
		concurrent buildtools_build linguisttools_build
ICON_SIZES=	14x14 16x16 22x22 24x24 32x32 36x36 48x48 64x64 72x72 96x96 128x128 192x192 256x256 512x512

PLIST_FILES=	bin/qtox \
		share/applications/qTox.desktop \
		share/icons/hicolor/scalable/apps/qtox.svgz
.for SZ in ${ICON_SIZES}
PLIST_FILES+=	share/icons/hicolor/${SZ}/apps/qtox.png
.endfor

pre-everything::
	@${ECHO_MSG}
	@${ECHO_MSG} "Warning: qTox won't build if the option NaCl was selected for Tox!"
	@${ECHO_MSG}

post-patch:
	@${REINPLACE_CMD} -e 's|$$$$system(git rev-parse HEAD)|"${GH_TAGNAME}"|' \
		${WRKSRC}/qtox.pro
	@${REINPLACE_CMD} -e 's|INCLUDEPATH += "/usr/include|INCLUDEPATH += "${LOCALBASE}/include|' \
		${WRKSRC}/qtox.pro
	@${REINPLACE_CMD} -e 's|INCLUDEPATH += "/usr/lib64|INCLUDEPATH += "${LOCALBASE}/lib|' \
		${WRKSRC}/qtox.pro
	@${REINPLACE_CMD} -e 's|INCLUDEPATH += "/usr/lib|INCLUDEPATH += "${LOCALBASE}/lib|' \
		${WRKSRC}/qtox.pro

pre-configure:
	@${REINPLACE_CMD} '/Comment/s,=.*,=${COMMENT},' \
		${WRKSRC}/qTox.desktop

post-install:
	${MKDIR} ${STAGEDIR}${PREFIX}/share/icons/hicolor/scalable/apps
	@${GZIP_CMD} ${GZIP} < ${WRKSRC}/img/icons/qtox.svg > ${STAGEDIR}${PREFIX}/share/icons/hicolor/scalable/apps/qtox.svgz
.for SZ in ${ICON_SIZES}
	@${MKDIR} ${STAGEDIR}${PREFIX}/share/icons/hicolor/${SZ}/apps
	@${CP} ${WRKSRC}/img/icons/qtox-${SZ}.png ${STAGEDIR}${PREFIX}/share/icons/hicolor/${SZ}/apps/qtox.png
.endfor

.include <bsd.port.mk>
