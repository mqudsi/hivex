# hivex Ruby bindings
# Copyright (C) 2009-2011 Red Hat Inc.
#
# This program is free software; you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation; either version 2 of the License, or
# (at your option) any later version.
#
# This program is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
#
# You should have received a copy of the GNU General Public License
# along with this program; if not, write to the Free Software
# Foundation, Inc., 675 Mass Ave, Cambridge, MA 02139, USA.

EXTRA_DIST = \
	Rakefile.in \
	README.rdoc \
	doc/site/index.html \
	ext/hivex/extconf.rb \
	ext/hivex/_hivex.c \
	lib/hivex.rb \
	run-ruby-tests \
	tests/tc_*.rb

CLEANFILES = \
	lib/*~ \
	tests/*~ \
	ext/hivex/*~ \
	ext/hivex/extconf.h \
	ext/hivex/_hivex.o \
	ext/hivex/_hivex.so \
	ext/hivex/mkmf.log \
	ext/hivex/Makefile

if HAVE_RUBY

TESTS = run-ruby-tests

TESTS_ENVIRONMENT = \
	LD_LIBRARY_PATH=$(top_builddir)/src/.libs \
	RUBY=$(RUBY) RAKE=$(RAKE)

all:
	$(RAKE) build
	$(RAKE) rdoc

RUBY_SITELIB := $(shell $(RUBY) -rrbconfig -e "puts Config::CONFIG['sitelibdir']")
RUBY_SITEARCH := $(shell $(RUBY) -rrbconfig -e "puts Config::CONFIG['sitearchdir']")

install:
	$(MKDIR_P) $(DESTDIR)$(RUBY_SITELIB)
	$(MKDIR_P) $(DESTDIR)$(RUBY_SITEARCH)
	$(INSTALL) -p -m 0644 lib/hivex.rb $(DESTDIR)$(RUBY_SITELIB)
	$(INSTALL) -p -m 0755 ext/hivex/_hivex.so $(DESTDIR)$(RUBY_SITEARCH)

endif
