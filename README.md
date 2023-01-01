# Writing Templates

Here are Markdown blog writing templates that add include support to Markdown. Makefiles are included to build the final document in multiple formats.

## General usage

1. Clone the repository
2. Copy (recursively) the macOS or Linux folder
3. Edit `main.md`
4. Images go in the `img` folder. Accepted formats are JPG and PNG. Add your image to your Markdown post as you normally would, e.g. `![](./img/cat.jpg)`
5. Code samples (code, snippets, etc) go in the `inc` folder. You can reference these files with `include({{example.js}})` (without `inc` in the path).

For example:

    Check out this awesome code:

    include({{example.js}})

Renders as:

    Check out this awesome code:

    ```javascript
    console.log("Hey!")
    ```

Make targets:
- `make post`: creates a Markdown file with the included files
- `make txt`: creates a plain text document without images
- `make docx`: creates a Word document.

Check `README.md` on the appropiate folder for more info. Windows users should install WSL and use the Linux template.

For a more detailed explanation check [this blog post](https://tomfern.com/post/writing-in-markdown).

