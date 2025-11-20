# CLAMS Documentation Hub

This directory contains the source files for the CLAMS documentation hub built with Sphinx.

## Building Documentation Locally

### Setup

```bash
# Create virtual environment
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate

# Install dependencies
pip install -r ../requirements.txt
```

### Build

```bash
# From the repository root
sphinx-build documentation docs-build

# Or from this directory
sphinx-build . ../docs-build
```

The built HTML will be in the `docs-build/` directory.

### View Locally

```bash
# Simple HTTP server
cd docs-build
python -m http.server 8000
# Then open http://localhost:8000 in your browser
```

## Structure

```
documentation/
├── conf.py           # Sphinx configuration
├── index.rst         # Homepage
├── team.rst          # Team page
├── events.rst        # Events page
├── cite.rst          # Citation information
├── _static/          # Static assets (images, CSS)
└── _build/           # Local build directory (gitignored)
```

## Phases

- **Phase 1** (Current): Basic Sphinx setup with hub pages
- **Phase 2**: SDK documentation integration
- **Phase 3**: Complete migration, deprecate Jekyll

## GitHub Actions

Documentation is automatically built and committed to `docs-build/` on push to main branch.

See `.github/workflows/build-sphinx-docs.yml` for details.
