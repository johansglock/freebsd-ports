# Created by: TAKATSU Tomonari <tota@FreeBSD.org>
# $FreeBSD$

PORTNAME=	knitr
PORTVERSION=	1.12.3
CATEGORIES=	print
DISTNAME=	${PORTNAME}_${PORTVERSION}

MAINTAINER=	tota@FreeBSD.org
COMMENT=	General-Purpose Package for Dynamic Report Generation in R

LICENSE=	GPLv2+

RUN_DEPENDS=	R-cran-evaluate>=0.8:${PORTSDIR}/devel/R-cran-evaluate \
		R-cran-digest>0:${PORTSDIR}/security/R-cran-digest \
		R-cran-formatR>0:${PORTSDIR}/textproc/R-cran-formatR \
		R-cran-highr>0:${PORTSDIR}/textproc/R-cran-highr \
		R-cran-markdown>0:${PORTSDIR}/textproc/R-cran-markdown \
		R-cran-stringr>=0.6:${PORTSDIR}/textproc/R-cran-stringr \
		R-cran-yaml>=2.1.5:${PORTSDIR}/textproc/R-cran-yaml

USES=	cran:auto-plist

.include <bsd.port.mk>
