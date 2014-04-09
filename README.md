pip-presentation
================

What is pip?
----
* **the** package manager for Python
* "The PyPA recommended tool for installing Python packages"
* comes with most distributions and Python 3.4+
* docs: http://www.pip-installer.org/en/latest/


What can you do with pip?
----
* `pip install <package>`
* `pip uninstall <package>`
* `pip search <term or package>`
* `pip install -U/--upgrade <package>`
* `pip freeze` show installed packages
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


ways to install a package
----
- `pip install packages` (default)
 - searches on pypi.python.org
- specify version of package
 - `pip install package==0.2.1`
 - `pip install package<=0.2.0`
- install a tarballed package from elsewhere
 - `pip install <path/to/tarball>` locally (can also be a folder)
 - `pip install http://<URL>` via http(s)
 - `pip install ssh://<URL>` .. or ssh
- `pip install <package> -f <URL>` 
 - search on \<URL\> for \<package\>
 - supports versioning (e.g. `package-1.0.tar.gz`, `package-1.1.tar.gz`)


piftalls
----
- specifying version can conflict if **newer** version is/was installed -> use `virtualenv`
- installing w/ tarballs only checks if version != installed_version -> can **downgrade**
- when installing from a local folder keep in mind
 - `pip install package` searches on pypi.python.org
 - `pip install package/` from the folder
- pip sometimes raises exception when package name is wrong or not found -> check your package name



virtualenv
----
`virtualenv` virtual environment
- encapsulated from your default Python installation
- only install necessary packages
- mix different package or python versions and keep them separated
- create test environments
- no need for sudo

1. create new virtual environment 
 - `virtualenv <path/for/env>`
2. activate virtual environment (do not forget!!)
 - `source <path/for/evn>/bin/activate`
3. leave virtual environment
 - `deactivate`


your own package
----
- can be anything importable by Python (eg.: single file scripts, libraries, C-Extensions)
- only needs a setup.py which describes your package
- compile C/C++ Extensions on installation time
- deal with your dependencies
- examples: https://docs.python.org/2/distutils/examples.html

one file
----

    PackageFolder/
        foo.py
        setup.py

setup.py

```python
from setuptools import setup

setup(
    name="pypackage",
    py_modules=['foo'],
    version='0.1.0',
    )
```

#### pitfall
```python
import package
```
`ImportError`

Installing is just a fancy copying of files. The name given in setup.py does not correspond with the import.

```python
import foo
```
`works`

better
----

    PackageFolder/
        pypackage/
            __init__.py
            foo.py
        setup.py

setup.py

```python
from setuptools import setup

setup(
    name="pypackage",
    packages=['pypackage'],
    version='0.1.0',
    )
```
##### pitfall


```python
import pypackage

pypackage.foo.hello()
```
`AttributeError`
Solution 1:


```python
import pypackage.foo

pypackage.foo.hello()
```

Solution 2

in `package/__init__.py`

```python
import foo
```
or
```python
from foo import *
```
-> 
```python
import package

package.hello()
```


- TODO dependencies
- TODO MANIFEST.in



deployment with pip via git repositories
----
- `pip install git+https://github.com/noamraph/tqdm.git#egg=tqdm` install tqdm directly from GitHub
- TODO
- TODO: install from git via ssh,
- TODO: via local repo - pip install git+file://test needs to have the folder, branches like repo@develop ??


links
----
- http://xion.org.pl/2014/01/27/anathomy-of-a-python-package/
- semantic versioning http://semver.org/
