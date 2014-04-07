pip-presentation
================

What is pip?
----
* package manager for Python
* "The PyPA recommended tool for installing Python packages"
* comes with most distributions and from Python 3.4+

What can you do with pip?
----
* `pip install <package>`
* `pip uninstall <package>`
* `pip search <term or package>`
* `pip install -U/--upgrade <package>`

pip vs. apt-get
----
- - no update notifications
- - other non-python packages don't know about them 
- - second package manager
- + more packages available
- + up-to-date packages
- + easy to make your own package
- + install via PyPI, http(s), ssh, git, GitHub, Mercurial, file
- + make develope installation (softlink to the sources instead of copying)

virtualenv
----
`virtualenv` virtual environment
- encapsulated from your default Python installation
- only install necessary packages
- mix different package or python versions 
- create test environments
