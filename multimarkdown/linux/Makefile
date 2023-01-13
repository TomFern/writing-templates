.PHONY = all post clean doc docx txt plain

all: build/post.md build/post.docx build/post.txt
txt: build/post.txt
plain: build/post.txt
html: build/post.html
post: build/post.md
doc: build/post.docx
docx: build/post.docx

build/post.md: post.md
	mkdir -p img build build/inc build/img
	cp -r inc/* build/inc 2>/dev/null || true
	cp post.md build/one.mmd
	(cd build; multimarkdown -t mmd one.mmd > two.mmd)
	if [ -n "$(shell ls -A img 2>/dev/null)" ]; then \
		cp img/* build/img; \
		mogrify -background White -alpha Background -format jpg build/img/*.png || true; \
		rm build/img/*.png; \
		sed -i 's/.png/.jpg/g' build/two.mmd; \
	fi
	(cd build; pandoc -f markdown_mmd -t gfm two.mmd -o post.md)
	rm build/one.mmd build/two.mmd
	rm -r build/inc

clean:
	rm -rf build/

build/post.txt: build/post.md
	(cd build && pandoc -f gfm -t plain -o post.txt post.md)

build/post.html: build/post.md
	(cd build && pandoc -f gfm -t html -o post.html post.md)

build/post.docx: build/post.html
	(cd build && pandoc -f html -t docx -o post.docx post.html)

