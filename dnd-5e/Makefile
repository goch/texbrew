INCLUDES=$(shell find . -type f -name "*.tex")

all: draft-skel.pdf skel.pdf

draft-%.pdf: %.tex $(INCLUDES) gen-images
	xelatex -halt-on-error -jobname=`echo $@ | rev | cut -b5- | rev` "\def\isdraft{1}\input{$<}"
	xelatex -halt-on-error -jobname=`echo $@ | rev | cut -b5- | rev` "\def\isdraft{1}\input{$<}"

%.pdf: %.tex $(INCLUDES) gen-images
	xelatex -halt-on-error $<
	xelatex -halt-on-error $<

gen-images:
	cd assets/samples && make

clean:
	rm -f *.{aux,log,pdf,nav,out,snm,toc}

.PHONY: clean
