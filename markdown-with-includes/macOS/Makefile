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

build/post.md: post.md
	mkdir -p build/img/d
	cp img/* build/img || true
	sips -s format jpeg build/img/*.png --out build/img/ || true
	rm build/img/*.png || true
	/Applications/ImageOptim.app/Contents/MacOS/ImageOptim build/img/*.jpg || true
	m4 -E -I./ post.md > build/includes.md
	sed 's/.png/.jpg/g' < build/includes.md > build/post.md
	rm build/includes.md

build/post.txt: build/post.md
	(cd build && pandoc -f gfm -t plain -o post.txt post.md)

build/post.html: build/post.md
	(cd build && pandoc -f gfm -t html -o post.html post.md)

build/post.docx: build/post.html
	(cd build && pandoc -f html -t docx -o post.docx post.html)

