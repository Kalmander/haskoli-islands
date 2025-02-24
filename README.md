![edbook](https://github.com/edbook/haskoli-islands/workflows/edbook/badge.svg)
![GitHub tag (latest by date)](https://img.shields.io/github/v/tag/edbook/haskoli-islands?label=version)

# Instructions

This is a template for a web-based textbook/lecture notes for the University of Iceland's mathematics department, using sphinx (see sphinx-doc.org).

## Install with Poetry
See [Poetry docs](https://python-poetry.org/docs/#installation) for recommended install method.


```sh
poetry shell
poetry install
```

Remember to run `poetry install` each time the main branch is pulled to install new packages or packages that might have been updated.
## Manual build
You can manually build a particular project by passing the folder name as an argument, like so:
```
make build project=undirbuningur_stae
```
## Build all projects
For convenience or testing if all projects build correctly, run the following command:
```bash
make build-all
```
## Run development server
Run a dev server for local development. This will open a tab in your browser at http://localhost:8000 which will update each time you you save a document in the project being worked on in the [source](src/projects) directory. The build ends up in the `_build/your-project` where `your-project` is the project you are building.

```bash
make autobuild project=undirbuningur_stae
```

## Sagecell
All `*.sage` files should be added to `src/extensions/sagecell-extension/examples` directory so they can be reused across projects. You can continue to reference them by filename only.
## Contribute
The following rules should be followed when contributing:
- Create a branch (or fork the project if you are not already a contributor) from master
- Commit messages should follow the [Conventional Commits specs](https://www.conventionalcommits.org)

By using the _Conventional Commits specs_ the [semver](https://semver.org/) release tags _(major.minor.patch / 0.1.0)_ will be determined automatically based on the commit messages, e.g. `fix: changed some stuff` will bump the current version as a `patch` to `0.1.1`, as supposed to `feat: added a new chapter` will bump the current version as a `minor` to `0.2.0`.

Breaking changes, e.g. `BREAKING CHANGE: replacing RestructuredTEXT with Markdown in Sphinx` will bump the current version as a `major` release to `1.1.0`.

[Commitizen](https://commitizen-tools.github.io/commitizen/) already comes installed as a dev-dependency to help you out with this. Instead of using `git commit -a -m "feat: some feature"` you can use the _Committizen CLI_ which will prompt options in the terminal.

```sh
cz commit
```


**TODO: needs work**

Each time you push changes to the remote branch a [pre-release](https://github.com/busla/undirbuningur_stae/releases) will be created and deployed to `https:/notendur.hi.is/some-user/path/to/branch`.


When the project owners merge the feature branch to master an automatic release will be created and deployed to production.


## Install without virtualenv
For ubuntu based distros run the following commands in the terminal:

```bash
sudo apt-get install python3-sphinx
sudo apt-get install python3-sphinx-rtd-theme
sudo apt-get install python3-setuptools
sudo apt-get install python3-sagecell
sudo apt-get install git
sudo apt-get install pandoc
git clone https://github.com/edbook/template
```
There should now be a template folder in /home/user. The following folders are in the template folder:

* sagecell-extension
* toggleblock-extension
* ggbextension
* SphinxScrolldepth
* hoverrole

In each of these folders run the following commands:
```bash
python3 setup.py build
sudo python3 setup.py install
```

Sphinx
======
Information on how to install sphinx can be found here: http://sphinx-doc.org/latest/install.html

Instructions for getting started with sphinx are here: http://sphinx-doc.org/latest/tutorial.html

This template comes with a source directory, conf.py file with the values set as we found convenient for Mathematical Analysis I (the aprropriate project title and author name need to be inserted in certain places in the file), makefile, and a slightly modified version of the Read the Docs theme (https://docs.readthedocs.org/en/latest/theme.html) with Icelandic language settings and the Univeristy of Iceland and Raunvísindadeils logos. It is therefore not necessary to run sphinx-quickstart to set up the project.


Pandoc
======
Sphinx generates html and latex files from rst files.
Pandoc can be used to convert files from tex to rst (and convert between many other filetypes)

Information on pandoc installation can be found at http://pandoc.org/installing.html.

A command like the following can then be used to convert latex to rst (more info at http://pandoc.org):

pandoc -t rst filename.tex -o filename.rst

A few things to have in mind when using pandoc to convert latex to rst:

-   The conversion ignores commands such as \block, \frame, \theorem, and \proof
    You might want to replace such commands with \section, \subsection, \subsubsection, \paragraph, \subaparagraph before conversion.

-   math ($...$) within bold/italicized text sections


Sphinx extensions
=================
Many extensions have been written to add features and modifications to sphinx projects.
Several extensions come bundled with sphinx: http://sphinx-doc.org/extensions.html

Three custom extensions come with this framework (ggbextension to embed geogebra applets, toggleblock-extension for toggleable text sections and sagecell-extension to embed sage cells. See README files in the extension folders.)
