include ../common/common.mk

all:

MAKEFILE := Makefile-loesung
include ../common/recursive.mk

all: $(BUILDS)
	@rm -rf build
	@mkdir -p build/exercises-latex-{1,2,3}
	@cp -r 01-helloworld 02-input 03-lists 04-titlepage 05-structure build/exercises-latex-1
	@cp -r 06-math 07-siunitx build/exercises-latex-2
	@cp -r 08-figures 09-tables 10-references 11-biblatex build/exercises-latex-3
	@rm -rf build/exercises-latex-{1,2,3}/*/{{,*/}{Makefile,.gitignore},*/__pycache__}
	@cd build ; \
	for day in 1 2 3 ; do \
		cd exercises-latex-$$day ; \
		for dir in * ; do \
			cd "$$dir" && mv build/loesung.pdf . && rm -rf build && cd .. || true ; \
		done ; \
		cd .. ; \
		echo zip -rq exercises-latex-$$day.zip exercises-latex-$$day ; \
		zip -rq exercises-latex-$$day.zip exercises-latex-$$day ; \
	done

clean:
	git clean -Xdf

.PHONY: all clean
