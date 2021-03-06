====================================
Static HTML Output Documentation
====================================

`Sphinx <https://www.sphinx-doc.org>`_ powered documentation project for `Static HTML Output <https://statichtmloutput.com>`_, using `reStructuredText <https://docutils.readthedocs.io/en/sphinx-docs/user/rst/quickstart.html>`_.

Served generously by `ReadTheDocs <https://readthedocs.org>`_.

**Contributing**

You can choose to either:

- fork this repository and edit directly in browser on GitHub, submit pull request
- fork this repository and edit on your computer, submit pull request

To build locally, a `requirements.txt` is provided so you can reproduce the same Python environment used by other contributors.

- `git clone git@github.com:WP2Static/statichtmloutput-docs.git`
- `cd statichtmloutput-docs`
- `virtualenv venv` (don't track this dir in git)
- `source venv/bin/activate`
- `pip3 install -r requirements.txt`
- `cd docs`
- `make html` (outputs site to `_build/html`

**(Optional) edit diagrams locally**

`PlantUML <https://plantuml.com/>`_ is used for generating rich image diagrams, while remaining editable 
within this repository.

You'll need to install the `.jar` file into the docs dir as `plantuml.jar` and 
can get `latest version here <http://sourceforge.net/projects/plantuml/files/plantuml.jar/download>`_. This is not tracked under git, as there is a version available on ReadTheDocs. `Learn more <https://sphinxcontrib-needs.readthedocs.io/en/latest/installation.html#install-plantuml>`_. A Java runtime will also be required to use PlantUML.

`plantuml` should be available on your `PATH`. You can either set a fully resolvable path in this repo's `docs/conf.py` file or add a wrapper as below:

.. code-block:: shell

  % cat <<EOT > /usr/local/bin/plantuml
  #!/bin/sh -e
  java -jar /path/to/plantuml.jar "$@"
  EOT
  % chmod +x /usr/local/bin/plantuml

Depending on the type of diagrams being used, you'll probably also need `graphviz` installed in your host operating system.

**Forcing rebuild of docs locally**

- `cd docs`
- `make clean`
- `make html`


**Need help?**

With contributing documentation or actually using Static HTML Output, please use our `Forum <https://staticword.press>`_.
 
Everybody is welcome!

Cheers,

`Leon Stafford <https://ljs.dev>`_
