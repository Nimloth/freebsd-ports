# Created by: tcberner
# $FreeBSD$

PORTNAME=	kservice
PORTVERSION=	${KDE_FRAMEWORKS_VERSION}
CATEGORIES=	devel kde kde-frameworks

MAINTAINER=	kde@FreeBSD.org
COMMENT=	KF5 advanced plugin and service introspection

USES=		bison cmake:outsource compiler:c++11-lib gettext kde:5 tar:xz
USE_KDE=	archive config coreaddons crash dbusaddons \
		doctools ecm i18n
USE_QT5=	buildtools_build core dbus gui qmake_build xml

.include <bsd.port.mk>
