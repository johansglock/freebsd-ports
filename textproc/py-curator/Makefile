# Created by: Dan Langille <dvl@FreeBSD.org>
# $FreeBSD$

PORTNAME=		curator
PORTVERSION=		3.4.0
DISTVERSIONPREFIX=	v
CATEGORIES=		textproc python
PKGNAMEPREFIX=		${PYTHON_PKGNAMEPREFIX}

MAINTAINER=		dvl@FreeBSD.org
COMMENT=		Python index manager for Elasticsearch

LICENSE=		APACHE20

RUN_DEPENDS=	${PYTHON_PKGNAMEPREFIX}urllib3>=1.8.3:${PORTSDIR}/net/py-urllib3 \
		${PYTHON_PKGNAMEPREFIX}elasticsearch-py>=1.8.0:${PORTSDIR}/textproc/py-elasticsearch-py \
		${PYTHON_PKGNAMEPREFIX}click>=3.3:${PORTSDIR}/devel/py-click

USE_GITHUB=	yes
GH_ACCOUNT=	elastic
USES=		python
USE_PYTHON=	distutils autoplist

.include <bsd.port.mk>
