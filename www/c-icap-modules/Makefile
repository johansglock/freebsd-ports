# Created by: Martin Matuska <mm@FreeBSD.org>
# $FreeBSD$

PORTNAME=	c-icap
PORTVERSION=	0.4.2
PORTREVISION=	1
CATEGORIES=	www security
MASTER_SITES=	SF/${PORTNAME}/${PORTNAME}${PKGNAMESUFFIX}/0.4.x/
PKGNAMESUFFIX=	-modules
DISTNAME=	c_icap_modules-${PORTVERSION}

MAINTAINER=	mm@FreeBSD.org
COMMENT=	Modules for c-icap: virus_scan and srv_url_check

LICENSE=	GPLv2+
LICENSE_FILE=	${WRKSRC}/COPYING

LIB_DEPENDS+=	libicapapi.so:${PORTSDIR}/www/c-icap \
		libclamav.so:${PORTSDIR}/security/clamav

USES=		libtool
GNU_CONFIGURE=	yes
INSTALL_TARGET=	install-strip
DATADIR=	${PREFIX}/share/c_icap

CFLAGS+=	-DHAVE_STRNSTR

CONFIGURE_ARGS+=	--enable-static \
			--with-c-icap=${LOCALBASE} \
			--with-clamav=${LOCALBASE}

pre-install:
	@${MKDIR} ${STAGEDIR}${PREFIX}/etc/c-icap

.include <bsd.port.mk>
