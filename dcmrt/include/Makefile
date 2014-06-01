#
#	Makefile for dcmrt/include
#



SHELL = /bin/sh
srcdir = .
top_srcdir = ..
configdir = ../../config

include $(configdir)/Makefile.def


all:

install: 
	$(configdir)/mkinstalldirs $(DESTDIR)$(includedir)/dcmtk/dcmrt
	for file in dcmtk/dcmrt/*.h ; do \
		$(INSTALL_DATA) $$file $(DESTDIR)$(includedir)/dcmtk/dcmrt ;\
	done
	$(configdir)/mkinstalldirs $(DESTDIR)$(includedir)/dcmtk/dcmrt/seq
	for file in dcmtk/dcmrt/seq/*.h ; do \
		$(INSTALL_DATA) $$file $(DESTDIR)$(includedir)/dcmtk/dcmrt/seq ;\
	done

clean:
	rm -f $(TRASH)

distclean:
	rm -f $(DISTTRASH)
