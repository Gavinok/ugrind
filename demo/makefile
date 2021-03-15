# Neatroff settings
BASE = $(HOME)/.local/share/neat
ROFF = $(BASE)/neatroff/roff
POST = $(BASE)/neatpost/post

ROFFOPTS = -F$(BASE) -M$(BASE)/tmac
POSTOPTS = -F$(BASE) -pa4
GSOPTS = -dPDFSETTINGS=/prepress -dEmbedAllFonts=true \
		-sFONTPATH=$(BASE)/fonts/ -sFONTMAP=$(BASE)/fonts/Fontmap 

# Ugrind settings
UGRIND = ../ugrind
UGRINDDEFS = ../ugrindefs
PRE = soelim | $(UGRIND) -d $(UGRINDDEFS)

# Target
MACROS = -ms
ROFFEXT = tr
.SUFFIXES: .$(ROFFEXT) .tr .ps .pdf .PDF .html

all: ugrind.pdf

.ps.pdf:
	@ps2pdf $(GSOPTS) $< $@

.$(ROFFEXT).ps:
	cat $< | $(PRE) | $(ROFF) $(ROFFOPTS) $(MACROS) | $(POST) $(POSTOPTS) >$@

clean:
	rm -f *.ps *.pdf

.PHONY: clean all lint test
