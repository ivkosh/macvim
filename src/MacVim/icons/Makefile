.PHONY: clean getenvy

OUTDIR ?= .

$(OUTDIR)/MacVim-generic.icns: make_icons.py vim-noshadow-512.png loadfont.so 
	$(MAKE) -C makeicns
	/usr/bin/python make_icons.py $(OUTDIR)

loadfont.so: loadfont.c
	ARCHFLAGS='-arch x86_64 -arch i386' /usr/bin/python setup.py install --install-lib .

getenvy: Envy\ Code\ R\ Bold.ttf

Envy\ Code\ R\ Bold.ttf: EnvyCodeR.zip
	unzip -jo EnvyCodeR.zip
	# unzip uses the file date from the zip file. Change the file date to
	# "now", so that the zip is not unzipped in every `make` run.`
	touch Envy\ Code\ R\ Bold.ttf

ENVYCODE_URL=http://download.damieng.com/fonts/original/EnvyCodeR-PR7.zip
EnvyCodeR.zip:
	curl ${ENVYCODE_URL} --location -o EnvyCodeR.zip

clean:
	$(MAKE) -C makeicns clean
	rm -f $(OUTDIR)/MacVim-*.icns loadfont.so *.pyc \
	  EnvyCodeR.zip *.ttf *.reg *.txt
	rm -rf *.egginfo build  # Created by setup.py
