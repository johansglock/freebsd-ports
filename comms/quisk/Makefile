# Created by: Stephen Hurd <shurd@FreeBSD.org>
# $FreeBSD$

PORTNAME=	quisk
PORTVERSION=	4.0.1
CATEGORIES=	comms hamradio
MASTER_SITES=	http://james.ahlstrom.name/quisk/ \
		LOCAL/shurd

MAINTAINER=	hamradio@FreeBSD.org
COMMENT=	Software Defined Radio (SDR)

LICENSE=	GPLv2

LIB_DEPENDS=	libfftw3.so:${PORTSDIR}/math/fftw3 \
		libportaudio.so:${PORTSDIR}/audio/portaudio \
		libasound.so:${PORTSDIR}/audio/alsa-lib \
		libpulse.so:${PORTSDIR}/audio/pulseaudio

USES=		python
USE_PYTHON=	distutils autoplist
USE_WX=		3.0+
WX_COMPS=	python

post-extract:
	${RM} ${WRKSRC}/_quisk.so ${WRKSRC}/sdriqpkg/sdriq.so

post-patch:
	${REINPLACE_CMD} -e 's|%%LOCALBASE%%|${LOCALBASE}|g' ${WRKSRC}/setup.py

.include <bsd.port.mk>
