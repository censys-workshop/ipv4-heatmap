NAME=censys
INPUT=data/unique-ipv4-10262023-sorted-fixed.txt
Z=4

all: ${NAME}-z${Z}.png ${NAME}-blocklist-z${Z}.png  ## Create all images

${NAME}-z${Z}.png: ${NAME}.annotations ${NAME}.shade  ## Create a heatmap
	cat ${INPUT} | ../../ipv4-heatmap \
	  -s ${NAME}.shade \
	  -a ${NAME}.annotations \
	  -f /usr/X11R6/lib/X11/fonts/TTF/luximr.ttf \
	  -z ${Z}
	mv map.png $@

${NAME}-blocklist-z${Z}.png: ${NAME}.annotations ${NAME}.shade  ## Create a heatmap with blocklist shading
	cat ${INPUT} | ../../ipv4-heatmap \
	  -s ${NAME}-blocklist.shade \
	  -a ${NAME}.annotations \
	  -f /usr/X11R6/lib/X11/fonts/TTF/luximr.ttf \
	  -z ${Z}
	mv map.png $@

clean:  ## Remove generated files
	rm ${NAME}-z${Z}.png ${NAME}-blocklist-z${Z}.png

# via https://marmelab.com/blog/2016/02/29/auto-documented-makefile.html
.PHONY: help
help:
	@grep -E '^[a-zA-Z_-]+:.*?## .*$$' $(MAKEFILE_LIST) | sort | awk 'BEGIN {FS = ":.*?## "}; {printf "\033[36m%-30s\033[0m %s\n", $$1, $$2}'
