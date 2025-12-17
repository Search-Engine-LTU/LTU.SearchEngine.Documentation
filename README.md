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