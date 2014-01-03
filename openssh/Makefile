#
# CDDL HEADER START
#
# The contents of this file are subject to the terms of the
# Common Development and Distribution License, Version 1.0 only
# (the "License").  You may not use this file except in compliance
# with the License.
#
# You can obtain a copy of the license at COPYING
# See the License for the specific language governing permissions
# and limitations under the License.
#
# When distributing Covered Code, include this CDDL HEADER in each
# file and include the License file at COPYING.
# If applicable, add the following below this CDDL HEADER, with the
# fields enclosed by brackets "[]" replaced with your own identifying
# information: Portions Copyright [yyyy] [name of copyright owner]
#
# CDDL HEADER END
#
# Copyright (c) 2013, Alex Wilson.  All rights reserved.
#

VER =	openssh-6.4p1

include ../Makefile.defs

LIBDIR=                $(DESTDIR)/usr/lib/ssh
USRBINDIR=             $(DESTDIR)/usr/bin
BINDIR=                $(DESTDIR)/bin
MANDIR=                $(DESTDIR)/usr/share/man

PATCHES=       openssl_sunw.patch \
               openssl_sunw2.patch \
               umac_alias.patch

AUTOCONF_OPTS= \
	--prefix=/usr \
	--sysconfdir=/etc/ssh \
	--sbindir=/usr/lib/ssh \
	--libexecdir=/usr/lib/ssh \
	--with-solaris-contracts \
	--with-solaris-projects \
	--with-pam \
	--with-ssl-engine \
	--with-mantype=man

include ../Makefile.targ

all: all_autoconf

install: all
	( cd $(VER.32); \
	    gmake $(PARALLEL) DESTDIR=$(DESTDIR) install)
	mkdir -p $(MANDIR)/man4
	mkdir -p $(MANDIR)/man1m
	mv $(MANDIR)/man5/ssh_config.5 $(MANDIR)/man4/ssh_config.4
	mv $(MANDIR)/man5/sshd_config.5 $(MANDIR)/man4/sshd_config.4
	mv $(MANDIR)/man8/sshd.8 $(MANDIR)/man1m/sshd.1m
	mv $(MANDIR)/man8/ssh-keysign.8 $(MANDIR)/man1m/ssh-keysign.1m
	mv $(MANDIR)/man8/sftp-server.8 $(MANDIR)/man1m/sftp-server.1m
