pip-presentation
================

What is pip?
----
* package manager for Python
* "The PyPA recommended tool for installing Python packages"
* comes with most distributions and from Python 3.4+
* [docs](http://www.pip-installer.org/en/latest/)


What can you do with pip?
----
* `pip install <package>`
* `pip uninstall <package>`
* `pip search <term or package>`
* `pip install -U/--upgrade <package>`
* only pip 1.3+ `pip show <package>` 


pip vs. apt-get
----
- - no update notifications
- - other non-python packages don't know about them 
- - second package manager
- + more packages available
- + up-to-date packages
- + easy to create and install your own packages (unlike a Debian package)
- + make develope installation (softlink to the sources instead of copying)
- + installs from various sources


ways to install a package / pip is versatile
----
- `pip install <package>` installs from pypi.python.org (most of the packages are there)
- `pip install <package>==<version>` install a specific version of the packages
 - **can conflict if newer version is/was installed** -> use `virtualenv`
- `pip install <path/to/local/package>` installs a locally availabe Python package
- needs to be a package (setup.py)
- can be in a tarball
- `pip install <package> -f <URL>` search on <URL> for a <package> tarball (supports versioning)
- `pip install git+https://github.com/noamraph/tqdm.git#egg=tqdm` install tqdm directly from GitHub

TODO: test if folder and tarball packages are always handled (like version controlling a tarball or having a folder on the http server)


virtualenv
----
`virtualenv` virtual environment
- encapsulated from your default Python installation
- only install necessary packages
- mix different package or python versions and keep them separated
- create test environments
- no need for sudo


your own package
----
- can be
 - single Python file 
 - Python module
 - Extension (C/C++)
 - Python and Shell scripts
- only needs a setup.py which describes your package (name and modules to incorporate)
- can compile C/C++ Extensions on installation time
- deal with your dependencies

deployment with pip via git repositories
----
- TODO
- TODO: install from git via ssh,
- TODO: via local repo - pip install git+file://test needs to have the folder, branches like repo@develop ??


links
----
- http://xion.org.pl/2014/01/27/anathomy-of-a-python-package/
