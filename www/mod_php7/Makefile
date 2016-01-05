CATEGORIES=	www devel
PKGNAMEPREFIX=	mod_

MAINTAINER=	nobody@example.com

PHP_PORT=	lang/php7
MASTERDIR=	${.CURDIR}/../../${PHP_PORT}

OPTIONS_DEFINE=	AP2FILTER
AP2FILTER_DESC=	Use Apache 2.x filter interface (experimental)
OPTIONS_EXCLUDE=	CGI CLI FPM EMBED

.include "${MASTERDIR}/Makefile"
