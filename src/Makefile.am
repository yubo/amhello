# -*- Makefile -*-
# AUTOMAKE

AM_CPPFLAGS = ${regular_CPPFLAGS} -I${abs_top_srcdir}/src
AM_CFLAGS = ${regular_CFLAGS}

# Not having Kbuild in Makefile.extra because it will already recurse
.PHONY: modules modules_install clean_modules

_kcall = -C ${kbuilddir} M=${abs_srcdir}

modules:
	@echo -n "amhello ${PACKAGE_VERSION} - Linux "
	@if [ -n "${kbuilddir}" ]; then ${MAKE} ${_kcall} --no-print-directory -s kernelrelease; fi;
	${AM_V_silent}if [ -n "${kbuilddir}" ]; then ${MAKE} ${_kcall} modules; fi;

modules_install:
	${AM_V_silent}if [ -n "${kbuilddir}" ]; then ${MAKE} ${_kcall} INSTALL_MOD_PATH=${DESTDIR} ext-mod-dir='$${INSTALL_MOD_DIR}' modules_install; fi;

clean_modules:
	${AM_V_silent}if [ -n "${kbuilddir}" ]; then ${MAKE} ${_kcall} clean; fi;

all-local: modules

install-exec-local: modules_install

clean-local: clean_modules

sbin_PROGRAMS = hello
hello_LDADD = libhello.la

lib_LTLIBRARIES = libhello.la
libhello_la_SOURCES = libhello.c

bin_PROGRAMS = hello
hello_SOURCES = hello.c
