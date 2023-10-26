NAME=censys
INPUT=data/unique-ipv4-10262023-sorted-fixed.txt

all: ${NAME}.png

${NAME}.png: ${NAME}.annotations ${NAME}.shade
	cat ${INPUT} | ../../ipv4-heatmap \
	  -s ${NAME}.shade \
	  -a ${NAME}.annotations \
	  -f /usr/X11R6/lib/X11/fonts/TTF/luximr.ttf
	mv map.png $@

${NAME}-z.png: ${NAME}.annotations ${NAME}.shade
	cat ${INPUT} | ../../ipv4-heatmap \
	  -m \
	  -s ${NAME}.shade \
	  -a ${NAME}.annotations \
	  -f /usr/X11R6/lib/X11/fonts/TTF/luximr.ttf
	mv map.png $@

clean:
	rm ${NAME}.png ${NAME}-z.png
