.PHONY = all post clean doc docx txt plain

all: build/post.md build/post.docx build/post.txt
txt: build/post.txt
plain: build/post.txt
html: build/post.html
post: build/post.md
doc: build/post.docx
docx: build/post.docx
clean: 
	rm -rf build

build/post.md: main.md
	mkdir -p build/img
	cp img/*. build/img/ || true
	mogrify -background White -alpha Background -format jpg build/public/$(PROJECT)/*.png
	rm build/img/*.png
	m4 -E -I./ main.md > build/post.md
	grep "] " build/post.md || true

build/post.txt: build/post.md
	(cd build && pandoc -f gfm -t plain -o post.txt post.md)

build/post.html: build/post.md
	(cd build && pandoc -f gfm -t html -o post.html post.md)

build/post.docx: build/post.html
	(cd build && pandoc -f html -t docx -o post.docx post.html)

