# FileMint
https://pypi.org/project/filemint/
This is the FileMint package, which provides utilities for generating test files in various formats.

```
filemint_package/          <- Project root
├── filemint/              <- Python package
│   ├── __init__.py
│   ├── generators.py
│   └── cli.py
├── tests/                 <- Tests directory
│   ├── __init__.py
│   └── test_generators.py
├── setup.py               <- Setup file
├── pyproject.toml         <- Build configuration
└── other config files...
```
## Contributors
This project is very new and has many ways it can be improved. 
I welcome all help from the open source community
If you would like to contribute, please follow the guide found at filemint_package/CONTRIBUTING.md
Thank you for your interest in contributing to my project.
## Running Tests

To run the tests:

1. Create and activate a virtual environment:

```bash
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate
```

2. Install the package in development mode:

```bash
pip install -e .
```

3. Run the tests:

```bash
pytest
```

## Using the Package

After installation, you can use the package in two ways:

### Command Line Interface

```bash
# Generate default set of test files (10 of each type)
filemint

# Specify output directory
filemint --output-dir my_test_files

# Specify number of each file type
filemint --csv 5 --txt 10 --bin 3 --invalid 2
```

### Python API

```python
import filemint

# Generate test files with default settings
files = filemint.generate_test_files(output_dir="test_files")

# Generate a single CSV file
csv_file = filemint.generate_csv("output_dir", "data.csv", num_rows=20)
```

## Publishing to PyPI

See the PUBLISH.md file for detailed instructions on how to publish this package to PyPI. 
