# Created by: Edwin Groothuis <edwin@mavetju.org>
# $FreeBSD$

PORTNAME=	dnscap
PORTVERSION=	1.4.0
PORTEPOCH=	1
CATEGORIES=	dns
MASTER_SITES=	https://www.dns-oarc.net/files/dnscap/ \
		LOCAL/sunpoet

MAINTAINER=	sunpoet@FreeBSD.org
COMMENT=	DNS network traffic capture utility

LICENSE=	BSD3CLAUSE
LICENSE_FILE=	${WRKSRC}/LICENSE

OPTIONS_DEFINE=	DOCS

CONFIGURE_ARGS=	--enable-shared --enable-static --enable-threads
GNU_CONFIGURE=	yes
INSTALL_TARGET=	install-strip
USES=		libtool

PORTDOCS=	*

post-patch-DOCS-off:
	@${REINPLACE_CMD} -e '/^install-data-am: / s| install-dist_docDATA||' ${WRKSRC}/Makefile.in

.include <bsd.port.mk>
