# CLAMS Project Documentation

This repository contains the source for the CLAMS project documentation, built with [Sphinx](https://www.sphinx-doc.org/en/master/).

## Local Development

### Setup

To build the documentation locally, you'll need Python and `pip`.

1.  **Create and activate a virtual environment:**

    ```bash
    python -m venv venv
    source venv/bin/activate  # On Windows use `venv\Scripts\activate`
    ```

2.  **Install dependencies:**

    ```bash
    pip install -r requirements.txt
    ```

### Building the Documentation

To compile the documentation, run the following command from the root of the repository:

```bash
sphinx-build documentation docs-build
```

The generated HTML files will be in the `docs-build/` directory.

### Viewing the Documentation

You can preview the generated site locally using a simple Python web server:

```bash
cd docs-build
python -m http.server
```

Then, open `http://localhost:8000` in your web browser.

## Repository Structure

-   `documentation/`: Contains the Sphinx source files (`.rst`).
-   `docs-build/`: Contains the generated HTML output. This directory is committed to the repository to be served by GitHub Pages.
-   `requirements.txt`: Lists the Python dependencies required to build the documentation.
-   `.github/workflows/`: Contains the GitHub Actions workflow for automatically building the documentation.