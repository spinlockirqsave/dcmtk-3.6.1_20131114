#
#	Makefile for dcmrt/tests
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

LOCALINCLUDES = -I$(top_srcdir)/include -I$(dcmdatadir)/include -I$(oflogdir)/include \
	-I$(ofstddir)/include
LIBDIRS = -L$(top_srcdir)/libsrc -L$(dcmdatadir)/libsrc -L$(oflogdir)/libsrc \
	-L$(ofstddir)/libsrc
LOCALLIBS = -ldcmrt -ldcmdata -loflog -lofstd $(ZLIBLIBS) $(ICONVLIBS)

test_objs = tests.o tsearch.o
objs = drttest.o $(test_objs)
progs = drttest tests


all: $(progs)

drttest: drttest.o
	$(CXX) $(CXXFLAGS) $(LIBDIRS) $(LDFLAGS) -o $@ $@.o $(LOCALLIBS) $(MATHLIBS) $(LIBS)

tests: $(test_objs)
	$(CXX) $(CXXFLAGS) $(LIBDIRS) $(LDFLAGS) -o $@ $(test_objs) $(LOCALLIBS) $(ICONVLIBS) $(LIBS)

install: all


check: tests
	./tests


clean:
	rm -f $(objs) $(progs) $(TRASH)

distclean:
	rm -f $(objs) $(progs) $(DISTTRASH)


dependencies:
	$(CXX) -MM $(defines) $(includes) $(CPPFLAGS) $(CXXFLAGS) *.cc  > $(DEP)

include $(DEP)
