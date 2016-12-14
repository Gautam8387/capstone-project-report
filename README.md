# LaTeX template for TUM dissertations/PhD theses

An _unofficial_ Latex template for TUM dissertations/PhD theses that aims to satisfy the new [2016 corporate design guidelines of the TUM](https://portal.mytum.de/corporatedesign/index_html) regarding titlepage header and color usage.

Made by Andre Richter with help from [his colleagues](#contributions).

For a preview of the cover, [click here](#cover-preview). For a full preview, see the [PDF](dissertation.pdf).

##### Docker image info
[![](https://images.microbadger.com/badges/image/andrerichter/tum-dissertation-latex.svg)](https://microbadger.com/images/andrerichter/tum-dissertation-latex)

## Getting started

The following instructions work with Linux, macOS and Windows, because a Docker image is used that provides the whole build environment.

1. First of all, logos are needed. To circumvent copyright problems, they must be downloaded and cropped manually.
  1. Login at https://portal.mytum.de/corporatedesign/index_html/vorlagen/index_Logos
  2. Download the **SVG version** of the blue TUM logo and save it to `inc/`
  3. Download the **SVG version** of your faculty's logo and save it to `inc/`
2. Install Docker on your system. Find install instructions or binaries for your OS [here](https://www.docker.com/products/overview#/install_the_platform)
  - Windows users only: [Share the local drive](https://docs.docker.com/docker-for-windows/#/shared-drives). Right-click on the Docker icon in the bottom right gives you access to the settings.
3. Once Docker is installed, logos must be cropped and placed.
  1. Start a terminal/console/command and navigate where you saved the repository.
  2. Linux/macOS: Execute `make crop`
  3. Windows: Execute `make.bat crop`

_The command in the last step will first pull the Docker image from remote, which will take a couple of minutes. Fortunately, this must only be done once._

If everything worked, your setup is complete now and you are good to go!

## Building the PDF

### Linux/macOS
In a terminal, execute

- `make` to build the pdf.
- `make clean` to clean up temporary files.

### Windows
In a cmd or powershell, execute

- `make.bat` to build the pdf.
- `make.bat clean` to clean up temporary files.

*Double-clicking `make.bat` in the explorer also builds the pdf.*

## Troubleshooting

### Linux/macOS
- If you get errors one the `make` commands, you can try to invoke them via sudo, e.g. `sudo make crop`

## Template Usage

- At the top of `dissertation.tex`, you'll find parameters for the titlepage, e.g. names, faculty name, dissertation title, etc.
  - Also, have a look at the two binding correction options!
- Use `\captionabove{}` instead of `\caption{}` if you place a caption above a figure.
- Easy usage of TUM CI colors is provided by the tumcolors package. See `doc/tumcolor.pdf` for instructions.

## Compatibility

The TUM design guidelines lack explicit statements about how to place non-quadratic faculty logos. Each faculty logo has at least a partial circle. Most likely, the logo must be centered to the center of the logo's partial circle, and scale the diameter of the partial circle to 10mm. At least this is what we can derive from looking at page 16 of the [style guide](https://portal.mytum.de/corporatedesign/regeln/index_styleguide/styleguide/Manual_CD_2016_v1).

## TODOs

- [ ] Error handling in `crop_place_logos.sh` (missing binaries, files not found, etc.).
- [ ] Improve the windows batch file.

## Building without Docker

Linux/macOS users who want to build without Docker most likely know what to do. Dependencies can be found inside `Dockerfile`.
The `Makefile` already has targets for building without docker, just make them default.

## Contributions

Andre Richter - <andre.richter@tum.de>
- Makefile
- Title page design
- Plot cycle list
- Figures, tables, acronyms in table of contents
- Added a customized bibliography style based on [unsrturl.bst](http://ctan.mackichan.com/biblio/bibtex/contrib/urlbst/unsrturl.bst) that abbreviates first names
- Appendix support
- TUM color syntax highlighting for source code listings
- Siunitx styles
- Support for non-quadratic faculty logos

Michael Vonbun - <michael.vonbun@tum.de>
- tumcolors package
- Various cls file tweaks
- Latexmk support
- Sans serif title page option

Christian Herber - <christian.herber@tum.de>
- Barchart cycle list with pattern styles
- Table of contents in pdf index hack

Stefan Wallentowitz - <stefan.wallentowitz@tum.de>
- Prevent orphans and widows

Andreas Oeldemann - <andreas.oeldemann@tum.de>
- Help with Docker support.

## License

![Creative Commons License](https://i.creativecommons.org/l/by-sa/4.0/88x31.png)

This work is licensed under a [Creative Commons Attribution-ShareAlike 4.0 International License](http://creativecommons.org/licenses/by-sa/4.0/).

See [license file](LICENSE.md) for details.

## Cover Preview

<kbd>
![Cover Preview](/../preview/preview.png?raw=true "Cover Preview")
</kbd>
