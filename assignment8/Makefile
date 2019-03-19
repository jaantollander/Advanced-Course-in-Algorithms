BUILDDIR=build
FILE=assignment8

pdf:
	mkdir $(BUILDDIR) -p
	pandoc $(FILE).md \
	--from=markdown+raw_tex+tex_math_single_backslash+tex_math_dollars \
	--to=latex \
	--output=$(BUILDDIR)/$(FILE).pdf \
	--pdf-engine=xelatex \
	--variable urlcolor=cyan \
	--variable papersize=a4paper \
	--filter pandoc-citeproc \
	--bibliography=bibliography.bib \

clean:
	rm $(BUILDDIR)/*
