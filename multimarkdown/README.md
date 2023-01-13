# Multimarkdown templates

## Usage

1. Clone the repository and cd into this directory
2. Copy (recursively) the macOS or Linux folder
3. Edit `post.md`
4. Images go in the `img` folder. Accepted formats are JPG and PNG. Add your image to your MultiMarkdown post as you normally would, e.g. `![](./img/cat.jpg)`
5. Code samples (code, snippets, etc) go in the `inc` folder. You can reference these files with: `{{inc/some_other_file.txt}}`

For example:

    Check out this awesome code:

    {{inc/example.js}}

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

