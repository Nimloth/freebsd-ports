# $FreeBSD$

PORTNAME=	varnish
PORTVERSION=	4.1.3
PORTREVISION=	0
CATEGORIES=	www
MASTER_SITES=	http://repo.varnish-cache.org/source/
PKGNAMESUFFIX=	4

MAINTAINER=	feld@FreeBSD.org
COMMENT=	High-performance HTTP accelerator

LICENSE=	BSD2CLAUSE

LIB_DEPENDS=	libpcre.so:devel/pcre

CONFLICTS=	varnish-2.* varnish-3.*
BROKEN_arm=	does not configure

USES=		autoreconf cpe gmake libedit libtool pathfix pkgconfig python:2,build \
		readline shebangfix
SHEBANG_FILES=	lib/libvcc/vmodtool.py
CPE_VENDOR=	varnish-cache
CFLAGS+=	-I${LOCALBASE}/include
GNU_CONFIGURE=	yes
CONFIGURE_ARGS=	--localstatedir=${PREFIX} --enable-tests
CONFIGURE_ENV=	RST2MAN=true
USE_LDCONFIG=	yes
INSTALL_TARGET=	install-strip

USERS=		varnish varnishlog
GROUPS=		varnish

USE_RC_SUBR=	varnishd varnishlog varnishncsa
SUB_FILES=	pkg-message
.if defined(NO_INET6) || defined(WITHOUT_INET6)
BAD_TESTS+=	r00832
EXTRA_PATCHES+=	${FILESDIR}/no-inet6.patch
.endif

post-patch:
.if defined(BAD_TESTS)
	${RM} ${BAD_TESTS:C|.+|${WRKSRC}/bin/varnishtest/tests/\0.vtc|}
.endif

regression-test check test: build
	${MAKE_CMD} TESTS_PARALLELISM=1 -C ${WRKSRC} check

.include <bsd.port.mk>
