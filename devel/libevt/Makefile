# Created by: Antoine Brodin <antoine@FreeBSD.org>
# $FreeBSD$

PORTNAME=	libevt
DISTVERSION=	alpha-20160107
CATEGORIES=	devel
MASTER_SITES=	https://github.com/libyal/libevt/releases/download/${PORTVERSION:E}/ \
		LOCAL/antoine

MAINTAINER=	antoine@FreeBSD.org
COMMENT=	Library and tooling to access the Windows Event Log (EVT) format

LICENSE=	LGPL3

LIB_DEPENDS=	libregf.so:${PORTSDIR}/devel/libregf

GNU_CONFIGURE=	yes
CONFIGURE_ARGS=	--enable-python --with-libintl-prefix=${LOCALBASE} --with-libregf=${LOCALBASE}
USES=		gettext libtool pathfix python
USE_LDCONFIG=	yes
INSTALL_TARGET=	install-strip
WRKSRC=		${WRKDIR}/${PORTNAME}-${PORTVERSION:E}

PORTDOCS=	AUTHORS ChangeLog

OPTIONS_DEFINE=	DOCS

post-install-DOCS-on:
	@${MKDIR} ${STAGEDIR}${DOCSDIR}
	${INSTALL_DATA} ${PORTDOCS:S,^,${WRKSRC}/,} ${STAGEDIR}${DOCSDIR}

.include <bsd.port.mk>
