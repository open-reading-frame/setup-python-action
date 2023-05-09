# setup-python-action

This action is intended to be used by other actions/workflows to setup a given python environment. It will run python setup (default is version 3.10) by wrapping the [actions/setup-python action](https://github.com/actions/setup-python/), install python requirements given a `requirements.txt` file path and/or list of python packages, and cache dependency installation appropriately. Wildcards may be used for the path to the `requirements.txt` file(s). Note that if a `requirements.txt` file is not explicitly given, the action defaults to using either a `requirements.txt` or `pyproject.toml` file's hash as the cache key. If neither are present, caching will be disabled.

#### Setup Python 3.10

```yaml
- name: Install and set up Python 3.10
  uses: open-reading-frame/setup-python-action@main
```

#### Setup Python 3.x

```yaml
- name: Install and set up Python 3.x
  uses: open-reading-frame/setup-python-action@main
  with:
    python-version: 3.x
```

#### Install Specific Python Dependencies

```yaml
- name: Checkout source tree
  uses: actions/checkout@v3
- name: Install and set up Python 3.10 and install dependencies
  uses: open-reading-frame/setup-python-action@main
  with:
    requirements-txt: path/to/requirements.txt
    packages: <package 1> <package 2> ...
```

#### Install Wildcard Python Dependencies

```yaml
- name: Checkout source tree
  uses: actions/checkout@v3
- name: Install and set up Python 3.10 and install dependencies
  uses: open-reading-frame/setup-python-action@main
  with:
    requirements-txt: '**/requirements.txt'
```
