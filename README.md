# CLAMS Project Documentation Hub

This repository serves as the central publication hub for all documentation related to the CLAMS project. It aggregates generated HTML documentation from various source repositories and serves them from a single location.

## Structure

-   `index.html`: The main landing page for the entire documentation hub.
-   `.github/workflows/`: Contains the GitHub Actions workflows that automate the process of fetching, building, and publishing documentation from other repositories.
-   `docs/`: This directory contains all the generated documentation, organized by project and version.
    -   `docs/<project-name>/<version>/`: Contains the actual HTML files for a specific version of a project.
    -   `docs/<project-name>/latest/`: A stable URL that always points to the most recent version of a project's documentation.

## How It Works

The documentation source code (e.g., `.rst` files, Python docstrings) resides in the individual project repositories. A GitHub Actions workflow in this repository is responsible for:

1.  Checking out the source from a project repository.
2.  Building the HTML documentation using tools like Sphinx.
3.  Committing the generated HTML files to the appropriate directory within the `docs/` folder of this repository.

This repository does not contain any documentation *source* files, only the final, published HTML artifacts.
