# Writing Templates

Here are Markdown blog writing templates that add include support to Markdown. Makefiles are included to build the final document in multiple formats.

## General usage

- **Images**: go in the img folder. Accepted formats are jpg and png. Add your image to your Markdown post as you normally would, e.g. `![](./img/cat.jpg)`
- **Includes**: included files (code, snippets, etc) go in the inc folder. To add the contents of the file in your main Markdown document use `include({{example.js}})` (without `inc` in the path).

Make targets:
- `make post`: creates a Markdown file with the included files
- `make txt`: creates a plain text document without images
- `make docx`: creates a Word document.

Check `README.md` on the appropiate folder for more info. Windows users should install WSL and use the Linux template.

For a more detailed explanation check [this blog post]().

