TARGET = dronekey_report_personal
DIST_TARGET = dronekey_report_personal
CC = xelatex
BIB = bibtex
CCFLAGS = -shell-escape -synctex=1
TEXFILES = $(wildcard *.tex)

all: $(TARGET).pdf dist-clean wc

%.pdf:	$(TEXFILES) title/* files/* chapters/*
	@$(CC) $(CCFLAGS) $(TARGET)
	@$(CC) $(CCFLAGS) $(TARGET)


.PHONY:	clean all spell dist dist-clean wc


wc:
	texcount $(TARGET).tex


dist: clean all dist-clean
	sha256sum $(TARGET).pdf > $(TARGET).sha256sum
	mkdir -p $(DIST_TARGET)
	mv $(TARGET).pdf $(DIST_TARGET)
	mv $(TARGET).sha256sum $(DIST_TARGET)
	tar -czvf $(DIST_TARGET).tar.gz $(DIST_TARGET)
	rm -rf $(DIST_TARGET)



dist-clean:
	rm -f *log
	rm -f *aux
	rm -f *pyg
	rm -f *synctex.gz
	rm -f *bbl
	rm -f *blg
	rm -f *out

clean: dist-clean
	rm -f $(TARGET).pdf



spell:
	aspell -l en_uk --ignore-case=true -c $(TEXFILES)
