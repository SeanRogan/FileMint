# Contributing to FileMint

Thank you for considering contributing to FileMint! This document provides guidelines and instructions for contributing to this project.

## Development Environment Setup

1. Fork the repository on GitHub
2. Clone your fork locally:
   ```bash
   git clone https://github.com/yourusername/filemint.git
   cd filemint
   ```
3. Create a virtual environment and install development dependencies:
   ```bash
   python -m venv venv
   source venv/bin/activate  # On Windows: venv\Scripts\activate
   pip install -e ".[dev]"
   ```

## Development Workflow

1. Create a branch for your feature or bugfix:
   ```bash
   git checkout -b feature-name
   ```

2. Make your changes and follow these coding guidelines:
   - Follow PEP 8 style guidelines
   - Use meaningful variable and function names
   - Add docstrings to all functions, classes, and modules
   - Add type hints where appropriate
   - Add tests for new functionality

3. Run tests and linters:
   ```bash
   # Run all tests
   pytest
   
   # Run with coverage
   pytest --cov=filemint
   
   # Check code style
   black filemint tests
   isort filemint tests
   flake8 filemint tests
   mypy filemint
   ```

4. Commit your changes and push to your fork:
   ```bash
   git commit -m "Description of your changes"
   git push origin feature-name
   ```

5. Open a pull request from your fork to the main repository.

## Pull Request Guidelines

- Fill in the pull request template with all required information
- Ensure all tests pass and there are no linting errors
- Include tests for new functionality
- Update documentation if needed
- Keep pull requests focused on a single topic

## Code Style

This project uses:
- [Black](https://black.readthedocs.io/en/stable/) for code formatting
- [isort](https://pycqa.github.io/isort/) for import sorting
- [flake8](https://flake8.pycqa.org/en/latest/) for linting
- [mypy](https://mypy.readthedocs.io/en/stable/) for type checking

## Reporting Bugs

When reporting bugs, please include:
- Your operating system and Python version
- Steps to reproduce the bug
- Expected behavior
- Actual behavior
- Any relevant logs or screenshots

## Feature Requests

Feature requests are welcome! Please include:
- A clear description of the feature
- The motivation for adding the feature
- Possible implementation details (if you have ideas)

## Thank You!

Your contributions to open source, no matter how small, make projects like this possible. Thank you for taking the time to contribute. 