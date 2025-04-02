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
