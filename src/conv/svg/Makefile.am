bin_PROGRAMS = vsd2xhtml vss2xhtml

AM_CXXFLAGS = -I$(top_srcdir)/inc $(LIBVISIO_CXXFLAGS) $(DEBUG_CXXFLAGS)

vsd2xhtml_DEPENDENCIES = @VSD2XHTML_WIN32_RESOURCE@

vss2xhtml_DEPENDENCIES = @VSS2XHTML_WIN32_RESOURCE@

if STATIC_TOOLS

vsd2xhtml_LDADD = ../../lib/@VSD_OBJDIR@/libvisio-@VSD_MAJOR_VERSION@.@VSD_MINOR_VERSION@.a $(LIBVISIO_LIBS) @VSD2XHTML_WIN32_RESOURCE@
vsd2xhtml_LDFLAGS = -all-static

vss2xhtml_LDADD = ../../lib/@VSD_OBJDIR@/libvisio-@VSD_MAJOR_VERSION@.@VSD_MINOR_VERSION@.a $(LIBVISIO_LIBS) @VSS2XHTML_WIN32_RESOURCE@
vss2xhtml_LDFLAGS = -all-static

else

vsd2xhtml_LDADD = ../../lib/libvisio-@VSD_MAJOR_VERSION@.@VSD_MINOR_VERSION@.la $(LIBVISIO_LIBS) @VSD2XHTML_WIN32_RESOURCE@

vss2xhtml_LDADD = ../../lib/libvisio-@VSD_MAJOR_VERSION@.@VSD_MINOR_VERSION@.la $(LIBVISIO_LIBS) @VSS2XHTML_WIN32_RESOURCE@

endif

vsd2xhtml_SOURCES = \
	vsd2xhtml.cpp

vss2xhtml_SOURCES = \
	vss2xhtml.cpp

if OS_WIN32

@VSD2XHTML_WIN32_RESOURCE@ : vsd2xhtml.rc $(vsd2xhtml_OBJECTS)
	chmod +x $(top_srcdir)/build/win32/*compile-resource
	WINDRES=@WINDRES@ $(top_srcdir)/build/win32/lt-compile-resource vsd2xhtml.rc @VSD2XHTML_WIN32_RESOURCE@

@VSS2XHTML_WIN32_RESOURCE@ : vss2xhtml.rc $(vss2xhtml_OBJECTS)
	chmod +x $(top_srcdir)/build/win32/*compile-resource
	WINDRES=@WINDRES@ $(top_srcdir)/build/win32/lt-compile-resource vss2xhtml.rc @VSS2XHTML_WIN32_RESOURCE@
endif

EXTRA_DIST = \
	$(vsd2xhtml_SOURCES) \
	vsd2xhtml.rc.in \
	$(vss2xhtml_SOURCES) \
	vss2xhtml.rc.in

# These may be in the builddir too
BUILD_EXTRA_DIST = \
	vsd2xhtml.rc \
	vss2xhtml.rc
