all:	fr.htm fr.pdf unicode.htm unicode.pdf
fr.htm:
	pandoc fr.md -s -o fr.htm -t revealjs --mathjax --css=style.css -i
	sed -i "s|\/usr\/share\/javascript\/mathjax\/MathJax.js|mathjax\/MathJax.js|g" fr.htm

fr.pdf:
	pandoc fr.md -s -o fr.pdf -t beamer -i -V aspectratio=169 -V theme=Warsaw

unicode.htm:
	pandoc unicode.md -s -o unicode.htm -t revealjs --css=unicode.css -i

unicode.pdf:
	pandoc unicode.md -s -o unicode.pdf -t beamer -i -V aspectratio=169 -V theme=Warsaw --pdf-engine xelatex --variable mainfont="DejaVu Serif"

clean:
	rm fr.htm fr.pdf unicode.htm unicode.pdf
