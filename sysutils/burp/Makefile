# Created by: Loic Pefferkorn <loic-freebsd@loicp.eu>
# $FreeBSD$

PORTNAME=	burp
PORTVERSION=	1.4.40
CATEGORIES=	sysutils

MAINTAINER=	loic-freebsd@loicp.eu
COMMENT=	Network backup and restore program

LICENSE=	AGPLv3
LICENSE_FILE=	${WRKSRC}/LICENSE

BUILD_DEPENDS=	${LOCALBASE}/include/uthash.h:${PORTSDIR}/devel/uthash
LIB_DEPENDS=	librsync.so:${PORTSDIR}/net/librsync1

USE_GITHUB=	yes
GH_ACCOUNT=	grke

USE_RC_SUBR=	burp
GNU_CONFIGURE=	yes
USES=		gmake localbase ncurses

CONFIGURE_ARGS=	--sbindir="${PREFIX}/sbin" \
		--sysconfdir=${ETCDIR} \

CONFIG_FILES=	configs/server/burp.conf \
		configs/client/burp.conf \
		configs/certs/CA/CA.cnf

post-patch:
.for f in ${CONFIG_FILES}
	@${REINPLACE_CMD} -e 's,/etc/burp,${PREFIX}/etc/burp,g' ${WRKSRC}/${f}
	@${REINPLACE_CMD} -e 's,/usr/sbin,${PREFIX}/sbin,g' ${WRKSRC}/${f}
.endfor

post-install:
	@${STRIP_CMD} ${STAGEDIR}${PREFIX}/sbin/bedup
	@${STRIP_CMD} ${STAGEDIR}${PREFIX}/sbin/vss_strip
	@${STRIP_CMD} ${STAGEDIR}${PREFIX}/sbin/burp

.include <bsd.port.mk>
