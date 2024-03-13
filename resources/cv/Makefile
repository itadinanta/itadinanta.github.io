
.PHONY: cv
cv: nico_orru_cv.pdf

nico_orru_cv.pdf: ../../out/curriculum.pdf Makefile
	cp ../../out/curriculum.pdf nico_orru_cv.pdf

../../out/curriculum.pdf: curriculum.tex cvmacros.tex
	pdflatex -synctex=1 -output-format=pdf -output-directory=../../out curriculum.tex