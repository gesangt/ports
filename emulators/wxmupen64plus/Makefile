# Created by: Alonso Cardenas Marquez <acm@FreeBSD.org>
# $FreeBSD$

PORTNAME=	wxmupen64plus
PORTVERSION=	0.3
PORTREVISION=	3
CATEGORIES=	emulators
MASTER_SITES=	GOOGLE_CODE \
		LOCAL/acm/${PORTNAME} \
		http://cdn.bitbucket.org/auria/wxmupen64plus/downloads/
DIST_SUBDIR=	${PORTNAME:S/wx//}

MAINTAINER=	acm@FreeBSD.org
COMMENT=	Mupen64Plus 2.0 GUI frontend written using wxWidgets

BROKEN=		Unfetchable (google code has gone away)
DEPRECATED=	Unfetchable for more than six months (google code has gone away)
EXPIRATION_DATE=	2017-04-30

LIB_DEPENDS=	libmupen64plus.so.2:emulators/mupen64plus-core
RUN_DEPENDS=	${LOCALBASE}/lib/libmupen64plus.so.2:emulators/mupen64plus-core \
		${LOCALBASE}/lib/mupen64plus/mupen64plus-audio-sdl.so:emulators/mupen64plus-audio-sdl \
		${LOCALBASE}/lib/mupen64plus/mupen64plus-input-sdl.so:emulators/mupen64plus-input-sdl \
		${LOCALBASE}/lib/mupen64plus/mupen64plus-rsp-hle.so:emulators/mupen64plus-rsp-hle \
		${LOCALBASE}/lib/mupen64plus/mupen64plus-video-rice.so:emulators/mupen64plus-video-rice \
		mupen64plus:emulators/mupen64plus-ui-console

PROJECTHOST=	bsdistfiles
USES=		compiler:c++11-lib python
USE_CXXSTD=	c++11
USE_SDL=	yes
USE_WX=		3.0
WX_UNICODE=	yes
WAF_SCRIPT=	waf

post-patch:
	@${REINPLACE_CMD} -e 's|%%CC%%|${CC}|g' -e 's|%%CXX%%|${CXX}|g' -e \
		's|version=2.9|version=${WX_VERSION}|g' ${WRKSRC}/wscript

do-configure:
	@cd ${WRKSRC} && \
		${SETENV} CC="${CC}" CPP="${CPP}" CXX="${CXX}" \
		CFLAGS="${CFLAGS}" CPPFLAGS="${CPPFLAGS}" CXXFLAGS="${CXXFLAGS}" \
		LDFLAGS="${LDFLAGS}" ${PYTHON_CMD} ${WAF_SCRIPT} \
				configure --mupenapi=${LOCALBASE}/include/${PORTNAME:S/wx//} \
				--wxconfig=${WX_CONFIG} \
				--sdlconfig=${SDL_CONFIG} \
				--datadir=${DATADIR} \
				--libdir=${LOCALBASE}/lib/${PORTNAME:S/wx//}

do-build:
	@cd ${WRKSRC} && \
		${SETENV} ${MAKE_ENV} ${PYTHON_CMD} ${WAF_SCRIPT}

do-install:
	@${MKDIR} ${STAGEDIR}${DATADIR}
	@cd ${WRKSRC}/data && ${COPYTREE_SHARE} . ${STAGEDIR}${DATADIR}
	@${INSTALL_PROGRAM} ${WRKSRC}/build/${PORTNAME} ${STAGEDIR}${PREFIX}/bin/${PORTNAME}

.include <bsd.port.mk>
