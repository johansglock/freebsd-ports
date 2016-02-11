# Created by: Gea-Suan Lin <gslin@gslin.org>
# $FreeBSD$

PORTNAME=	memcached
PORTVERSION=	2.2.0
PORTREVISION=	8
CATEGORIES=	databases
PKGNAMEPREFIX=	php7-pecl-

USE_GITHUB=	yes
GH_ACCOUNT=	php-memcached-dev
GH_PROJECT=	php-memcached
GH_TAGNAME=	a2305d200638d58b24a743da139be2d655181ec0

MAINTAINER=	sunpoet@FreeBSD.org
COMMENT=	PHP extension for interfacing with memcached via libmemcached library

LICENSE=	PHP30

LIB_DEPENDS=	libmemcached.so:${PORTSDIR}/databases/libmemcached

OPTIONS_DEFINE=	IGBINARY SASL
IGBINARY_DESC=	Binary serializer support

CONFIGURE_ARGS=	--disable-memcached-sasl --with-libmemcached-dir=${LOCALBASE}
USE_PHP=	json session
USE_PHPEXT=	yes
USE_PHPIZE=	yes
USE_PHP_BUILD=	yes
USES=		pkgconfig tar:tgz

IGBINARY_CONFIGURE_ENABLE=	memcached-igbinary
IGBINARY_USE=		PHP=igbinary
SASL_CONFIGURE_ENABLE=	memcached-sasl
SASL_LIB_DEPENDS=	libsasl2.so:${PORTSDIR}/security/cyrus-sasl2

.include <bsd.port.mk>
