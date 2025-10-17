# uwcryoem.github.io

UW-Madison Cryo-EM HPC computing GitHub IO documentation site source.

See the site in action at [https://uwcryoem.github.io](https://uwcryoem.github.io).

## How to use

This documentation site uses Sphinx Docs to generate from the [reStructuredText](https://www.sphinx-doc.org/en/master/usage/restructuredtext/basics.html#rst-primer) Rich Text Formatting. Sphinx can also use the [Markdown](https://daringfireball.net/projects/markdown/) formatted text as a source with the 'myst_parser' extension.

### Create a virtual environment with the Sphinx documentation tools

```
python3 -m venv venv
source venv/bin/activate
python3 -m pip install -r requirements.txt
```

### Adding documentation 

Find the documentation source under `docsrc` folders. Then you can regenerate the overall `docs` production site with the `Makefile` command as below:

```
cd docsrc
make github
```

If you have the Sphinx tools in your python environment, this will be able to proceed to execute a Sphinx build for the documentation.
