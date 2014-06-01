#
#	Makefile for dcmdata/tests
#



SHELL = /bin/sh
VPATH = ../include:../../config/include
srcdir = .
top_srcdir = ..
configdir = ../../config

include $(configdir)/Makefile.def

ofstddir = $(top_srcdir)/../ofstd
oflogdir = $(top_srcdir)/../oflog

LOCALINCLUDES = -I$(top_srcdir)/include -I$(ofstddir)/include -I$(oflogdir)/include
LIBDIRS = -L$(top_srcdir)/libsrc -L$(top_srcdir)/libi2d -L$(ofstddir)/libsrc \
	-L$(oflogdir)/libsrc
LOCALLIBS = -ldcmdata -loflog -lofstd $(ZLIBLIBS) $(ICONVLIBS)
I2DLIBS = -li2d

objs = tests.o tpread.o ti2dbmp.o tchval.o tpath.o tvrdatim.o telemlen.o tparser.o \
	tdict.o tvrds.o tvrui.o tstrval.o tspchrs.o tvrpn.o tparent.o tfilter.o
progs = tests


all: $(progs)

tests: $(objs)
	$(CXX) $(CXXFLAGS) $(LIBDIRS) $(LDFLAGS) -o $@ $(objs) $(I2DLIBS) $(LOCALLIBS) $(LIBS)


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
