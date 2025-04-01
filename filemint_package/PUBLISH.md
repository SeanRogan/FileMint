# Publishing FileMint to PyPI

This guide explains how to build and publish the FileMint package to PyPI (Python Package Index) so others can install it using pip.

## Prerequisites

- You need a PyPI account (register at https://pypi.org/account/register/)
- You need to have the required development tools installed:
  ```bash
  pip install -e ".[dev]"
  ```

## Steps to Publish

### 1. Prepare your package

Make sure all changes are committed and your package is ready for release:

- Update version in `filemint/__init__.py`
- Update CHANGELOG.md (if you have one)
- Make sure tests pass: `pytest`

### 2. Build the package

```bash
python -m build
```

This will create both source distribution (`.tar.gz`) and wheel (`.whl`) in the `dist/` directory.

### 3. Test the package

Test that your package installs correctly from the built artifacts:

```bash
# Create a new virtual environment for testing
python -m venv test_env
source test_env/bin/activate  # On Windows: test_env\Scripts\activate

# Install your package from the local wheel
pip install dist/filemint-X.Y.Z-py3-none-any.whl

# Test that it works
filemint --csv 1 --txt 1 --bin 1 --invalid 1

# Exit the test environment
deactivate
```

### 4. Upload to Test PyPI (optional but recommended)

Before uploading to the real PyPI, you can test on TestPyPI:

```bash
python -m twine upload --repository-url https://test.pypi.org/legacy/ dist/*
```

Then test installation from TestPyPI:

```bash
pip install --index-url https://test.pypi.org/simple/ filemint
```

### 5. Upload to PyPI

When you're confident everything works, upload to the real PyPI:

```bash
python -m twine upload dist/*
```

You'll be prompted for your PyPI API key.

### 6. Verify the published package

After publishing, verify that your package can be installed from PyPI:

```bash
# Create a new virtual environment
python -m venv verify_env
source verify_env/bin/activate  # On Windows: verify_env\Scripts\activate

# Install from PyPI
pip install filemint

# Test that it works
filemint --csv 1 --txt 1 --bin 1 --invalid 1

# Exit the environment
deactivate
```

### 7. Create a GitHub Release (optional)

If your project is on GitHub, create a new release with a tag matching your version number.

## Automating releases with GitHub Actions

You can automate the release process using GitHub Actions. Create a workflow file in `.github/workflows/publish.yml`:

```yaml
name: Publish to PyPI

on:
  release:
    types: [created]

jobs:
  deploy:
    runs-on: ubuntu-latest
    steps:
    - uses: actions/checkout@v3
    - name: Set up Python
      uses: actions/setup-python@v4
      with:
        python-version: '3.x'
    - name: Install dependencies
      run: |
        python -m pip install --upgrade pip
        pip install build twine
    - name: Build and publish
      env:
        TWINE_USERNAME: ${{ secrets.PYPI_USERNAME }}
        TWINE_PASSWORD: ${{ secrets.PYPI_PASSWORD }}
      run: |
        python -m build
        twine upload dist/*
```

This workflow will automatically build and publish your package whenever you create a new release on GitHub. 