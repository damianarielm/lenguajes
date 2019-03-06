all:	fr.htm fr.pdf
fr.htm:
	pandoc fr.md -s -o fr.htm -t revealjs --mathjax --css=style.css -i
	sed -i "s|\/usr\/share\/javascript\/mathjax\/MathJax.js|mathjax\/MathJax.js|g" fr.htm

fr.pdf:
	pandoc fr.md -s -o fr.pdf -t beamer -i -V aspectratio=169 -V theme=Warsaw
