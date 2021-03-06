# Created by: Kubilay Kocak <koobs@FreeBSD.org>
# $FreeBSD$

PORTNAME=	pytest-xdist
PORTVERSION=	1.13.1
CATEGORIES=	devel python
MASTER_SITES=	CHEESESHOP
PKGNAMEPREFIX=	${PYTHON_PKGNAMEPREFIX}

MAINTAINER=	koobs@FreeBSD.org
COMMENT=	Py.test plugin for distributed testing and loop-on-failing modes

LICENSE=	MIT
LICENSE_FILE=	${WRKSRC}/LICENSE

BUILD_DEPENDS=	${PYTHON_PKGNAMEPREFIX}setuptools_scm>=0:${PORTSDIR}/devel/py-setuptools_scm
RUN_DEPENDS=	${PYTHON_PKGNAMEPREFIX}execnet>=1.1:${PORTSDIR}/sysutils/py-execnet \
		${PYTHON_PKGNAMEPREFIX}pytest>=2.4.2:${PORTSDIR}/devel/py-pytest \
		${PYTHON_PKGNAMEPREFIX}py>=1.4.22:${PORTSDIR}/devel/py-py
TEST_DEPENDS=	${PYTHON_PKGNAMEPREFIX}pytest>=2.5.1:${PORTSDIR}/devel/py-pytest \
		${PYTHON_PKGNAMEPREFIX}pexpect>0:${PORTSDIR}/misc/py-pexpect

USES=		python
USE_PYTHON=	autoplist concurrent distutils

NO_ARCH=	yes

post-extract:
	${RM} -rf ${WRKSRC}/testing/__pycache__

do-test:
	@cd ${WRKSRC} && py.test

.include <bsd.port.mk>
