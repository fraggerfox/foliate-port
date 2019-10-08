# $FreeBSD$

PORTNAME=	foliate
PORTVERSION=	1.5.3
CATEGORIES=	wip deskutils

MAINTAINER=	fox@FreeBSD.org
COMMENT=	Simple and modern GTK eBook viewer

LICENSE=	GPLv3
LICENSE_FILE=	${WRKSRC}/COPYING

BUILD_DEPENDS=	appstream-util:devel/appstream-glib \
		gjs-console:lang/gjs
LIB_DEPENDS=	libwebkit2gtk-4.0.so:www/webkit2-gtk3
RUN_DEPENDS=	gjs-console:lang/gjs

USES=		desktop-file-utils gettext gnome localbase meson python:3.6+ shebangfix
USE_GNOME=	cairo gtk30 introspection

INSTALLS_ICONS=	yes

SHEBANG_FILES=	${WRKSRC}/build-aux/meson/postinstall.py \
		${WRKSRC}/src/assets/KindleUnpack/*.py

USE_GITHUB=	yes
GH_ACCOUNT=	johnfactotum

GLIB_SCHEMAS=	com.github.johnfactotum.Foliate.gschema.xml

post-patch:
	@${REINPLACE_CMD} -e 's/@PYTHON_VERSION@/${PYTHON_VERSION}/g' \
		${WRKSRC}/src/main.js

post-install:
	@${RLN} ${STAGEDIR}${PREFIX}/bin/com.github.johnfactotum.Foliate \
		${STAGEDIR}${PREFIX}/bin/foliate

.include <bsd.port.mk>
