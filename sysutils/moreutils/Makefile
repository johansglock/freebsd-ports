# Created by: Charlie Kester <corky1951@comcast.net>
# $FreeBSD$

PORTNAME=	moreutils
PORTVERSION=	0.57
CATEGORIES=	sysutils
MASTER_SITES=	DEBIAN_POOL
DISTNAME=	${PORTNAME}_${PORTVERSION}.orig

MAINTAINER=	sunpoet@FreeBSD.org
COMMENT=	Additional Unix utilities

LICENSE=	GPLv2

RUN_DEPENDS=	p5-IPC-Run>=0:${PORTSDIR}/devel/p5-IPC-Run

OPTIONS_DEFINE=	MANPAGES
OPTIONS_DEFAULT=MANPAGES
OPTIONS_SUB=	yes

ALL_TARGET=	errnos.h ${CANNED_MANPAGES:R}
USES=		perl5 shebangfix
WRKSRC=		${WRKDIR}/${PORTNAME}-${PORTVERSION}

MAKE_JOBS_UNSAFE=	yes

CANNED_MANPAGES=errno.1 \
		ifdata.1 \
		ifne.1 \
		isutf8.1 \
		lckdo.1 \
		mispipe.1 \
		moreutils-parallel.1 \
		pee.1 \
		sponge.1
PERL_MANPAGES=	chronic.1 \
		combine.1 \
		moreutils-ts.1 \
		vidir.1 \
		vipe.1 \
		zrun.1

SHEBANG_FILES=	${PERL_MANPAGES:R}

post-extract:
.for file in parallel.c parallel.docbook ts
	@${MV} ${WRKSRC}/${file} ${WRKSRC}/moreutils-${file}
.endfor

post-patch:
	@${REINPLACE_CMD} -e 's|parallel|moreutils-&|g' ${WRKSRC}/Makefile
	@${REINPLACE_CMD} -e 's|__APPLE__|__${OPSYS}__|' ${WRKSRC}/ifdata.c
	@cd ${FILESDIR}/ && ${CP} ${CANNED_MANPAGES} ${WRKSRC}/

post-build:
.for man in ${PERL_MANPAGES:R}
	${LOCALBASE}/bin/pod2man --center=" " --release="${PORTNAME}" ${WRKSRC}/${man} > ${WRKSRC}/${man}.1
.endfor

do-install:
	cd ${WRKSRC}/ && ${INSTALL_PROGRAM} ${CANNED_MANPAGES:R} ${STAGEDIR}${PREFIX}/bin/
	cd ${WRKSRC}/ && ${INSTALL_SCRIPT} ${PERL_MANPAGES:R} ${STAGEDIR}${PREFIX}/bin/
	cd ${WRKSRC}/ && ${INSTALL_MAN} ${CANNED_MANPAGES} ${PERL_MANPAGES} ${STAGEDIR}${PREFIX}/man/man1/

# maintainer section:
# require: docbook-xsl, libxml2, libxslt

updateman: do-clean extract
.for man in ${CANNED_MANPAGES:R}
	${LOCALBASE}/bin/xmllint --noout --valid ${WRKSRC}/${man}.docbook && \
	${LOCALBASE}/bin/xsltproc --output ${FILESDIR}/${man}.1 --param man.authors.section.enabled 0 ${LOCALBASE}/share/xsl/docbook/manpages/docbook.xsl ${WRKSRC}/${man}.docbook
.endfor
	${MV} ${FILESDIR}/parallel.1 ${FILESDIR}/moreutils-parallel.1

.include <bsd.port.mk>
