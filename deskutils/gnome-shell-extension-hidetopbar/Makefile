# Created by: Gustau Perez i Querol <gustau.perez@gmail.com>
# $FreeBSD$

PORTNAME=	gnome-shell-extension-hidetopbar
PORTVERSION=	0.0.0.20150613
CATEGORIES=	deskutils gnome
DIST_SUBDIR=	gnome3

MAINTAINER=	gnome@FreeBSD.org
COMMENT=	Hide the topbar except in overview mode

BUILD_DEPENDS=	gnome-shell>=0:${PORTSDIR}/x11/gnome-shell \
		gsettings-desktop-schemas>=3.12.0:${PORTSDIR}/devel/gsettings-desktop-schemas
RUN_DEPENDS=	gnome-shell>=0:${PORTSDIR}/x11/gnome-shell \
		gsettings-desktop-schemas>=3.12.0:${PORTSDIR}/devel/gsettings-desktop-schemas

USES=		gettext gmake pkgconfig tar:xz
USE_GNOME=	glib20
USE_GITHUB=	yes
CPPFLAGS+=	-I${LOCALBASE}/include
LDFLAGS+=	-L${LOCALBASE}/lib
GLIB_SCHEMAS=	org.gnome.shell.extensions.hidetopbar.gschema.xml

GH_ACCOUNT=	mlutfy
GH_PROJECT=	hidetopbar
GH_TAGNAME=	9758a91

PKGMESSAGE=	../gnome-shell-extra-extensions/pkg-message.slaves

NO_BUILD=	yes

do-install:
	@${MKDIR} ${STAGEDIR}${PREFIX}/share/glib-2.0/schemas/
	@${MKDIR} ${STAGEDIR}${PREFIX}/share/gnome-shell/extensions/hidetopbar@mathieu.bidon.ca
	${INSTALL_DATA} ${WRKSRC}/org.gnome.shell.extensions.hidetopbar.gschema.xml \
		${STAGEDIR}${PREFIX}/share/glib-2.0/schemas/
	@${RM} -fr ${WRKSRC}/org.gnome.shell.extensions.hidetopbar.gschema.xml
	cd ${WRKSRC} && ${COPYTREE_SHARE} . \
		${STAGEDIR}${PREFIX}/share/gnome-shell/extensions/hidetopbar@mathieu.bidon.ca/

.include <bsd.port.mk>
