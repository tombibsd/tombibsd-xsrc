#	$NetBSD$

# generate format_srgb.c

.include "../Makefile.inc"

SCRIPT=	${X11SRCDIR.MesaLib}/src/util/format_srgb.py
format_srgb.c: ${SCRIPT}
	${PYTHON} ${SCRIPT} > $@.tmp && mv $@.tmp $@
