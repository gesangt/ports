# Created by: Aaron Dalton <aaron@FreeBSD.org>
# $FreeBSD$

PORTNAME=	Petal
PORTVERSION=	2.24
CATEGORIES=	textproc perl5
MASTER_SITES=	CPAN
MASTER_SITE_SUBDIR=	CPAN:NINE
PKGNAMEPREFIX=	p5-

MAINTAINER=	perl@FreeBSD.org
COMMENT=	Perl Template Attribute Language - TAL for Perl!

LICENSE=	ART10 GPLv1
LICENSE_COMB=	dual

BUILD_DEPENDS=	p5-Locale-Maketext-Gettext>=0:devel/p5-Locale-Maketext-Gettext \
		p5-MKDoc-XML>=0.72:textproc/p5-MKDoc-XML
RUN_DEPENDS:=	${BUILD_DEPENDS}
TEST_DEPENDS=	p5-URI>=0:net/p5-URI

NO_ARCH=	yes
USES=		perl5
USE_PERL5=	configure

.include <bsd.port.mk>
