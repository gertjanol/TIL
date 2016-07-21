# PyPI

## Building and uploading django-eventhandler ([GitHub](https://github.com/ByteInternet/django-eventhandler/)/[PyPI](https://pypi.python.org/pypi/django-eventhandler))


[Create a private useraccount on test PyPI.](https://testpypi.python.org/pypi). For the real PyPI, we use a shared account 'byte'.

Create a file in your homedir, called `.pypirc`, with the following content
```
[distutils]
index-servers =
    pypi
    pypitest

[pypi]
repository = https://pypi.python.org/pypi
username = byte

[pypitest]
repository = https://testpypi.python.org/pypi
username = <username>
```

Then run:
```
# Bump version in setup.py
vim setup.py
git add setup.py
git commit -m "Bump version"
git push

# Tag with new version
git tag $version
git push --tags

# Create new build (source and wheel)
python setup.py sdist bdist_wheel

# Upload build to test pypi
pip install twine
twine upload -r pypitest dist/*

# Verify package new build is available https://testpypi.python.org/pypi/django-eventhandler

# Upload to real PyPI
twine upload -r pypi dist/*
```
