# Writing Practice

Generate custom writing practice sheets for young scribes using LaTeX. This project allows you to create printable PDF worksheets with tracing lines, perfect for children learning to write.

You can find an example of the generated practice sheets at `build/main.pdf` and write your own word list in a plain text file.

One shortcoming of this project is that scaling the letter/line size is not trivial. You can have to tweak a couple of parameters in `src/config.tex` to get the desired output.

## Prerequisites

Before you can build the practice sheets, you need to install a few tools.

### 1. TeX Live

You need a TeX distribution to compile the LaTeX code. We recommend **TeX Live**.

*   **Linux (Ubuntu/Debian)**:
    Open your terminal and run:
    ```bash
    sudo apt-get install texlive-full
    ```
    *Note: This installs the complete distribution (~5GB). For a smaller installation, `texlive-latex-extra` and `texlive-fonts-recommended` might be sufficient, but `texlive-full` guarantees all dependencies are met.*

*   **macOS**:
    If you have Homebrew installed, run:
    ```bash
    brew install --cask mactex
    ```
    Alternatively, download the [MacTeX installer](https://www.tug.org/mactex/).

*   **Windows**:
    Download and run the [TeX Live installer](https://www.tug.org/texlive/acquire-netinstall.html) (install-tl-windows.exe).

### 2. Fonts

This project uses the **KG Primary Penmanship** font. You must install it on your system for the document to compile correctly.

1.  **Download**: Get the font (e.g., from [DaFont](https://www.dafont.com/kg-primary-penmanship.font) or [Kimberly Geswein Fonts](https://www.kimberlygeswein.com/2012/11/16/kg-primary-penmanship/)).
2.  **Install**:
    *   **Windows/macOS**: unzip the downloaded file, double-click the `.ttf` or `.otf` files, and click **Install**.
    *   **Linux**:
        1.  Create a `.fonts` directory in your home folder if it doesn't exist:
            ```bash
            mkdir -p ~/.fonts
            ```
        2.  Copy the font files there (assuming they are in your Downloads folder):
            ```bash
            cp ~/Downloads/KGPrimaryPenmanship*.ttf ~/.fonts/
            ```
        3.  Update the font cache:
            ```bash
            fc-cache -fv
            ```

### 3. VS Code & LaTeX Workshop

We recommend using Visual Studio Code with the LaTeX Workshop extension for an easy editing and building experience.

1.  Install [Visual Studio Code](https://code.visualstudio.com/).
2.  Install the [LaTeX Workshop extension](https://marketplace.visualstudio.com/items?itemName=James-Yu.latex-workshop) by James Yu.

## Project Structure

*   `src/main.tex`: The main LaTeX file that generates the PDF.
*   `src/config.tex`: Configuration for page layout and fonts.
*   `src/words.txt`: The list of words to generate practice lines for.
*   `src/words.example.txt`: An example word list.

## How to Build

### Using VS Code (Recommended)

1.  Open this folder in VS Code.
2.	Create `src/words.txt` and add your own words similar to `src/words.example.txt`.
3.  Open `src/main.tex`.
4.  Open the **TeX** sidebar (icon with the TeX logo).
5.  Under **Commands**, click **Build LaTeX project**.
6.  Once built, click **View LaTeX PDF** -> **View in VSCode tab** to preview your worksheet.

### Command Line

You can also build the project using `latexmk` (included with TeX Live).

```bash
cd src
latexmk -lualatex main.tex
```

The output `main.pdf` will be generated in the same directory (or `../build` if configured).
