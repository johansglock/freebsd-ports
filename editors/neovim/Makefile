# Created by: Anton Tornqvist <antont@inbox.lv>
# $FreeBSD$

PORTNAME=	neovim
PORTVERSION=	0.1.2
CATEGORIES=	editors
MASTER_SITES=	GH

MAINTAINER=	antont@inbox.lv
COMMENT=	Next generation Vim

LICENSE=	APACHE20

BUILD_DEPENDS=	${LUA_MODSHAREDIR}/MessagePack.lua:${PORTSDIR}/devel/lua-MessagePack \
		${LUA_MODLIBDIR}/bit.so:${PORTSDIR}/devel/lua-bitop \
		${LUA_MODLIBDIR}/lpeg.so:${PORTSDIR}/devel/lua-lpeg
LIB_DEPENDS=	libunibilium.so:${PORTSDIR}/devel/unibilium \
		libvterm.so:${PORTSDIR}/devel/libvterm \
		libtermkey.so:${PORTSDIR}/devel/libtermkey \
		libluajit-5.1.so:${PORTSDIR}/lang/luajit \
		libuv.so:${PORTSDIR}/devel/libuv \
		libmsgpack.so:${PORTSDIR}/devel/msgpack

USES=		cmake gettext-tools lua gmake pkgconfig
USE_GITHUB=	yes
GH_TAGNAME=	b33c777

CMAKE_ARGS+=	-DLUA_PRG=${LUA_CMD} \
		-DUSE_BUNDLED_DEPS=OFF

.include <bsd.port.mk>
