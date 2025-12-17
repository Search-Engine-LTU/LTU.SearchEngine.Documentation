## 📝 Documentation / LaTeX Setup

### 1. Install Tools
To be able to create the PDF locally, you need two things:

* **A LaTeX engine:**
    * **Windows:** Download and install [MiKTeX](https://miktex.org/).
    * **Mac:** Download [MacTeX](https://www.tug.org/mactex/).
    * *Note: Restart VS Code after the installation!*
* **VS Code Extension:**
    * Search for **LaTeX Workshop** (by James Yu) in the Extensions tab and install it.

### 2. Configure VS Code (Important!)
To avoid error messages regarding "Perl" or "BibTeX" and to ensure the PDF builds automatically when you save, we need to add a custom "recipe".

1.  In VS Code, press `Ctrl` + `Shift` + `P`.
2.  Type **Open User Settings (JSON)** and press `Enter`.
3.  Paste the following settings into your file (ensure you have commas between lines if you already have other settings):

```json
"latex-workshop.latex.recipes": [
  {
    "name": "Generate PDF Only",
    "tools": ["pdflatex"]
  }
],
"latex-workshop.latex.tools": [
  {
    "name": "pdflatex",
    "command": "pdflatex",
    "args": [
      "-synctex=1",
      "-interaction=nonstopmode",
      "-file-line-error",
      "%DOC%"
    ]
  }
],
"latex-workshop.latex.recipe.default": "Generate PDF Only",
"latex-workshop.latex.autoBuild.run": "onSave",
"latex-workshop.latex.autoClean.run": "never",
"latex-workshop.latex.linting.chktex.enabled": false
```
### 3. Workflow
Open the file LTU_Search_Engine.tex.

Make your changes to the text.

Press Ctrl + S (Save).

Wait a few seconds. A new PDF will be generated automatically.

To view the PDF side-by-side with the code: Click the TeX icon in the left menu -> View LaTeX PDF -> View in VS Code tab.

### 4. Git Rules for Documentation
❌ DO NOT check in: .aux, .log, .out, .bbl (These should be automatically ignored by .gitignore).

✅ ALWAYS check in: The .tex file (source code) AND the .pdf file (so it can be read on GitHub without downloading the repository).

