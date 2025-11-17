# Documentation Hub Implementation Plan

This document outlines the current status and future implementation plan for the CLAMS Documentation Hub.

## 1. Goal

This repository is a **hybrid**. It serves two primary functions:
1.  It contains the source code and build process for the main documentation (`clams-main`).
2.  It acts as a central **publication hub** for the generated HTML from both itself and all external CLAMS subprojects.

## 2. Current Status

*   **Repository Structure:** A hybrid structure is now in place.
*   **Main Docs Source:** The Sphinx source for the `clams-main` documentation is located in the `documentation/` directory.
*   **Build Script:** A Python script at `build/main.py` exists to run the Sphinx build for the main documentation.
*   **Dependencies:** Build dependencies are located in `build/requirements.txt`.
*   **Generated Content:** The output for `clams-main` is located in `docs/clams-main/latest/`.
*   **Automation:** The GitHub Actions workflow is not yet functional and does not use the new build script.

## 3. Future Implementation Plan

The following steps will implement a robust, automated, and scalable architecture.

### Step 1: Automate the Main Documentation Build

The immediate next step is to create a functional GitHub Actions workflow that automates the build and deployment of the documentation sourced from this repository.

**Tasks:**
*   Update the workflow file at `.github/workflows/publish-docs.yml`.
*   This workflow will trigger on pushes to the `main` branch (e.g., when changes are made in `documentation/` or `build/`).
*   **The workflow will execute the following steps:**
    1.  Check out the repository.
    2.  Set up a Python environment.
    3.  Install the build dependencies from `build/requirements.txt`.
    4.  Run the main build script: `python build/main.py`.
    5.  Commit and push any changes within the `docs/` directory back to the repository.

### Step 2: Implement Build Process for Hub Landing Page

To make the hub's landing page dynamic, we will create a dedicated build script for it.

**Tasks:**
*   Create a `templates/` directory for Jinja2 templates (e.g., `index.html.j2`).
*   Create a `build/hub.py` script that uses Jinja2 to render the template into the root `index.html`. This will allow the landing page to be dynamically updated with links as new projects are added.
*   Add `Jinja2` to the `build/requirements.txt` file.
*   Update the main GHA workflow to also run `python build/hub.py`.

### Step 3: Integrate External Subprojects via Reusable Workflows

To add documentation from other repositories, we will use a modular and safe "reusable workflow" pattern.

**Tasks:**
*   Create a "callable" workflow file (e.g., `.github/workflows/build-external-doc.yml`). This workflow will be responsible for checking out an external repository, running its unique build process, and uploading the resulting HTML as a build artifact.
*   Update the main `publish-docs.yml` orchestrator workflow to:
    1.  Call the reusable workflow for each external subproject.
    2.  Include a final `publish` job that downloads all artifacts from the build jobs and commits them to the `docs/` directory in a single, safe transaction.
