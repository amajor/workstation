# Setup for Python

## Install Homebrew
Have homebrew installed.

## Install Python
```bash
brew install python

# Confirm it is working
python3 --version
```

## Install Pip
From [Geeks for Geeks](https://www.geeksforgeeks.org/how-to-install-pip-in-macos/):

```bash
# Download Pip
curl https://bootstrap.pypa.io/get-pip.py -o get-pip.py

# Execute the downloaded file
python3 get-pip.py

# Confirm its working
pip3 --version
```

## Install Virtual Environment
```bash
python3 -m pip install --user virtualenv
python3 -m virtualenv --help
```

# In Your Repository

## Create a Virtual Environment Directory
```bash
python3 -m virtualenv venv
```

This has now created a venv directory in your repository.

## Activate Virtual Environment

In order to work in your virtual environment, you need to activate it:

```shell
source venv/bin/activate
```

Now you'll see a `venv` reference in your terminal for every command.

To exit the virtual environment:

```shell
deactivate
```

## Install PyTest

```shell
pip install pytest
```

## Create a Setup File

In your root directory, create `setup.py`:

```shell
// Create setup.py
$ touch setup.py
```

Populate the file with the following:

```py
from setuptools import setup, find_packages

setup(
    name='the-great-developer-adventure',
    version='1.0.0',
    install_requires=[
        'pytest'
    ],
    packages=find_packages()
)
```

Back in your terminal (in your root folder), run your setup file:

```shell
// Run the setup
$ python3 setup.py develop
```

# Create a Tested Module

This is being run in the virtual environment that we created. You don't _have_ to run in a virtual environment, but then all dependencies will be installed globally.

## Make Directories and Initialze

We need to create a directory for our module and then initialize it. In this sample, we'll call it `samplecode`:

```shell
// Make the directory
$ mkdir samplecode

// Initialize as a Module
$ touch samplecode/__init__.py

// Create a test directory
$ mkdir tests
```

## Let's Make a Sample Code

We'll pretend it's a `utils.py` file:

```shell
// Move into your module folder, samplecode
cd samplecode

// Create a utils.py file
touch utils.py
```

Let's make a very simple method:

```py
def add(x, y):
    return x + y
```

## Let's make a test

Move back to the `tests` folder and make a test file. It's important to preceed the test file with `test_` so that our automatic script can find the file.

```shell
// Navigate into test folder.
$ cd ../tests

// Create test file for utils.py
$ touch test_utils.py
```

Edit your `test_utils.py` file with a test. First you must import your methd (`add` in our case). Then define your test (it must start with `test_` in the method name) using `assert` to set the expected outcome.

```py
from samplecode.utils import add

def test_add():
    assert add(10, 10) == 20
```

## Run the Test(s)

Navigate back to the root of your project and then run `pytest`.

```shell
// Navigate to the root (out of the test folder)
$ cd ..

// Run the tests
$ pytest
```

### Parameterize the Test

If you'd like to run multiple tests, we can easily paramterize our method:

```py
# test_utils.py contents
from samplecode.utils import add
import pytest

@pytest.mark.parametrize('x, y, result', [
    (10, 10, 20),
    (1, 2, 3),
    (5, 10, 15)
])
def test_add(x, y, result):
    assert add(x, y) == result
```
