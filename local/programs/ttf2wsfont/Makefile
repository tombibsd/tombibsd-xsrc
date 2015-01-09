#	$NetBSD$
#	@(#)Makefile	8.1 (Berkeley) 5/31/93

PROG=	ttf2wsfont

SRCS=	main.c
WARNS=	3

CPPFLAGS+=	-DXFREE86_FT2 -I${DESTDIR}${X11INCDIR}/freetype2

LDADD+=	-lfreetype

.include <bsd.x11.mk>
.include <bsd.prog.mk>
