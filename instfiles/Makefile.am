EXTRA_DIST = \
   keymap-names.txt \
   xrdp.sh \
   xrdp-sesman.service \
   xrdp.service

#
# files for all platforms
#
startscriptdir=$(sysconfdir)/xrdp

dist_startscript_DATA = \
  km-00000407.ini \
  km-00000409.ini \
  km-0000040a.ini \
  km-0000040b.ini \
  km-0000040c.ini \
  km-00000410.ini \
  km-00000411.ini \
  km-00000412.ini \
  km-00000414.ini \
  km-00000415.ini \
  km-00000416.ini \
  km-00000419.ini \
  km-0000041d.ini \
  km-00000807.ini \
  km-00000809.ini \
  km-0000080c.ini \
  km-00000813.ini \
  km-00000816.ini \
  km-0000100c.ini 

#
# platform specific files
#
SUBDIRS =
if LINUX
SUBDIRS += \
  pam.d \
  pulse
dist_startscript_SCRIPTS = xrdp.sh
if HAVE_SYSTEMD
dist_systemdsystemunit_DATA = \
  xrdp-sesman.service \
  xrdp.service
else
SUBDIRS += \
  default \
  init.d
endif # HAVE_SYSTEMD
endif # LINUX

if FREEBSD
SUBDIRS += \
  pam.d \
  rc.d \
  pulse
endif

#
# install-data-hook for each platform
#
if LINUX
# must be tab below
install-data-hook:
	if [ -f $(DESTDIR)$(sysconfdir)/init.d/xrdp ]; then \
		sed -i 's|__BASE__|$(prefix)|' $(DESTDIR)$(sysconfdir)/init.d/xrdp; \
	fi
endif

if FREEBSD
# must be tab below
install-data-hook:
	sed -i '' 's|%%PREFIX%%|$(prefix)|g' $(DESTDIR)$(sysconfdir)/rc.d/xrdp
endif
