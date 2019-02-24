slides.htm:
	pandoc slides.md -s -o slides.htm -t revealjs --mathjax --css=style.css -i

slides.pdf:
	pandoc slides.md -s -o slides.pdf -t beamer -i -V aspectratio=169 -V theme=Warsaw
