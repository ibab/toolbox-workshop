CATEGORIES := 01-helloworld 02-input 03-lists 04-titlepage 05-structure 06-math 07-siunitx 10-references 11-biblatex

all: package

exercises:
	for category in $(CATEGORIES) ; do \
		if [ -e "$$category/Makefile-loesung" ] ; then \
			make -C "$$category" -f Makefile-loesung ; \
		fi ; \
	done

package: exercises
	rm -rf build
	mkdir -p build/exercises-latex-{1,2,3,4}
	cp -r 01-helloworld 02-input 03-lists 04-titlepage 05-structure build/exercises-latex-1
	cp -r 06-math 07-siunitx build/exercises-latex-2
	cp -r 10-references 11-biblatex build/exercises-latex-3
	rm -f build/exercises-latex-{1,2,3,4}/*/Makefile
	rm -f build/exercises-latex-{1,2,3,4}/*/*/Makefile
	rm -f build/exercises-latex-{1,2,3,4}/*/.gitignore
	rm -f build/exercises-latex-{1,2,3,4}/*/*/.gitignore
	rm -rf build/exercises-latex-{1,2,3,4}/*/*/__pycache__
	cd build ; \
	for day in 1 2 3 4 ; do \
		cd exercises-latex-$$day ; \
		for dir in * ; do \
			cd "$$dir" && mv build/loesung.pdf . && rm -r build && cd .. || true ; \
		done ; \
		cd .. ; \
		zip -r exercises-latex-$$day.zip exercises-latex-$$day ; \
	done

clean:
	git clean -Xdf