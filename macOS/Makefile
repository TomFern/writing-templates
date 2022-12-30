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

build/post.md: main.md links.md
	mkdir -p build/img/
	sips -s format jpeg img/*.png --out build/img/ || true
	cp img/*.jpg img/*.jpeg build/img || true
	/Applications/ImageOptim.app/Contents/MacOS/ImageOptim build/img/*.jpg
	m4 -E -I./ main.md > build/out.md
	sed 's/img\//public\/$(PROJECT)\//g;s/.png/.jpg/g' < build/out.md > build/post.md
	rm build/out.md
	grep "] " build/post.md || true

build/post.txt: build/post.md
	(cd build && pandoc -f gfm -t plain -o post.txt post.md)

build/post.html: build/post.md
	(cd build && pandoc -f gfm -t html -o post.html post.md)

build/post.docx: build/post.html
	(cd build && pandoc -f html -t docx -o post.docx post.html)

