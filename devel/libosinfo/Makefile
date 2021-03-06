# Created by: Roman Bogorodskiy <novel@FreeBSD.org>
# $FreeBSD$

PORTNAME=	libosinfo
PORTVERSION=	0.3.0
CATEGORIES=	devel
MASTER_SITES=	https://fedorahosted.org/releases/l/i/libosinfo/

MAINTAINER=	novel@FreeBSD.org
COMMENT=	Library for managing OS information for virtualization

LIB_DEPENDS=	libsoup-gnome-2.4.so:${PORTSDIR}/devel/libsoup-gnome
BUILD_DEPENDS=	${LOCALBASE}/share/pciids/pci.ids:${PORTSDIR}/misc/pciids \
		${LOCALBASE}/share/usbids/usb.ids:${PORTSDIR}/misc/usbids
RUN_DEPENDS:=	${BUILD_DEPENDS}

USES=		gmake libtool pathfix pkgconfig
USE_GNOME=	glib20 libxml2 libxslt introspection:build intlhack
USE_LDCONFIG=	yes
GNU_CONFIGURE=	yes
INSTALL_TARGET=	install-strip

CONFIGURE_ARGS=	--disable-tests --disable-vala \
		--with-usb-ids-path=${LOCALBASE}/share/usbids/usb.ids \
		--with-pci-ids-path=${LOCALBASE}/share/pciids/pci.ids
CPPFLAGS+=	-I${LOCALBASE}/include
LIBS+=		-L${LOCALBASE}/lib

OPTIONS_DEFINE=	NLS
OPTIONS_SUB=yes

NLS_USES=	gettext
NLS_CONFIGURE_ENABLE=	nls

.include <bsd.port.mk>
