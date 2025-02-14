#python

#### Details
Free
Open Source
Cross Platform Compatible

### Versions
Python2 - 2000 to 2010
Python3 - 2008 to Present

`python2 -V`
`python3 -V`

### Install

 `yum install python2`
 `yum install python36`


### Running different versions if both are installed
`python2`
`python3`

### Python Commands
To run Python code or program:
`python2 main.py`


# PIP
#pip
Python Package Manager (pip)

### Versions
`pip2 -V`
`pip3 -V`

`pip -V` - can use this to determine which python install it is defaulting to

Intalling other apps:

`pip install flask`

`pip show flask` - this will give you all the information including the location of the package

Display all locations where Python interpreter will look for packages:
`python -c "import sys; print(sys.path"`

### Installing Other packages

`pip install flask`
`pip install jinja2`
`pip install markupsafe`
`pip install Werkzeug`
`pip install requests`
`pip install gunicorn`

`pip install flask jinja2 markupsafe`

You can also put all the package details inside of a requirements.txt and use the cmd below:
`pip install -r requirements.txt`

**requirements.txt:**
`Flask==0.10.1`
`Jinja2==2.7.3`
`MarkupSafe==0.23`
`Werkzeug==0.9.6
`requests==2.3.0
`gunicorn==18.0`

If not specifying version, it will install the latest. You should always use version numbers, as new version can break your application.

#### Upgrade Package
`pip install flask --upgrade`

Uninstall:
`pip uninstall flask`


## Other Package Managers

### easy_install
Uses app.py then converts to app.egg using setuptools

**Install with:** 
`easy_install install app`

### wheels
Uses app.py then converts to app.whl using setuptools

**Installs with:**
`pip install app.whl`