.POSIX:
.SUFFIXES:
.PHONY: all clean install check

PROJECT   =pickstyle
VERSION   =1.0.0
PREFIX    =/usr/local
BUILDDIR ?=.build

all:
clean:
install:
	mkdir -p $(DESTDIR)$(PREFIX)/share/styles
	cp share/styles/* $(DESTDIR)$(PREFIX)/share/styles
check:
## -- BLOCK:license --
install: install-license
install-license: README.md COPYING
	mkdir -p $(DESTDIR)$(PREFIX)/share/doc/$(PROJECT)
	cp README.md COPYING $(DESTDIR)$(PREFIX)/share/doc/$(PROJECT)
## -- BLOCK:license --
## -- BLOCK:sh --
install: install-sh
install-sh:
	mkdir -p $(DESTDIR)$(PREFIX)/bin
	cp bin/pickstyle $(DESTDIR)$(PREFIX)/bin
	cp bin/descstyle $(DESTDIR)$(PREFIX)/bin
install: install-share
install-share:
	mkdir -p $(DESTDIR)$(PREFIX)/share
	cp -r share/styles $(DESTDIR)$(PREFIX)/share
## -- BLOCK:sh --
