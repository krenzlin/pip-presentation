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
- + easy to create and install your own packages
- + installs via http(s), ssh, git, GitHub, Mercurial, file
- + make develope installation (softlink to the sources instead of copying)

ways to install a package
----
- `pip install <package>` installs from pypi.python.org (most of the packages are there)
- `pip install <package>==<version>` install a specific version of the packages
 - **can conflict if newer version is/was installed** -> use `virtualenv`
- `pip install <path/to/local/package>` installs a locally availabe Python package
- needs to be a package (setup.py)
- can be in a tarball
- `pip install <package> -f <URL>` search on <URL> for a <package> tarball (supports versioning)
- `pip install git+https://github.com/noamraph/tqdm.git#egg=tqdm` install tqdm directly from GitHub



virtualenv
----
`virtualenv` virtual environment
- encapsulated from your default Python installation
- only install necessary packages
- mix different package or python versions and keep them separated
- create test environments
- no need for sudo
