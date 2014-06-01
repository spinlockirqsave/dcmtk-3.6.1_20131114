#
#	Makefile for dcmsr/tests
#



SHELL = /bin/sh
VPATH = ../include:../../config/include
srcdir = .
top_srcdir = ..
configdir = ../../config

include $(configdir)/Makefile.def

ofstddir = $(top_srcdir)/../ofstd
oflogdir = $(top_srcdir)/../oflog
dcmdatadir = $(top_srcdir)/../dcmdata
dcmimgledir = $(top_srcdir)/../dcmimgle
dcmimagedir = $(top_srcdir)/../dcmimage

LOCALINCLUDES = -I$(ofstddir)/include -I$(oflogdir)/include -I$(dcmdatadir)/include \
	-I$(dcmimgledir)/include -I$(dcmimagedir)/include
LIBDIRS = -L$(top_srcdir)/libsrc -L$(ofstddir)/libsrc -L$(oflogdir)/libsrc \
	-L$(dcmdatadir)/libsrc -L$(dcmimgledir)/libsrc -L$(dcmimagedir)/libsrc
LOCALLIBS = -ldcmsr -ldcmimage -ldcmimgle -ldcmdata -loflog -lofstd $(TIFFLIBS) \
	$(PNGLIBS) $(XMLLIBS) $(ZLIBLIBS) $(ICONVLIBS)

tstobjs = tests.o tsrtree.o
objs = mkreport.o $(tstobjs)
progs = mkreport tests


all: $(progs)

mkreport: mkreport.o
	$(CXX) $(CXXFLAGS) $(LIBDIRS) $(LDFLAGS) -o $@ mkreport.o $(LOCALLIBS) $(MATHLIBS) $(LIBS)

tests: $(tstobjs)
	$(CXX) $(CXXFLAGS) $(LIBDIRS) $(LDFLAGS) -o $@ $(tstobjs) $(LOCALLIBS) $(MATHLIBS) $(LIBS)


check: tests
	./tests

install: all


clean:
	rm -f $(objs) $(progs) $(TRASH)

distclean:
	rm -f $(objs) $(progs) $(DISTTRASH)


dependencies:
	$(CXX) -MM $(defines) $(includes) $(CPPFLAGS) $(CXXFLAGS) *.cc  > $(DEP)

include $(DEP)
