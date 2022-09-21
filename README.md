# action-html-dir-to-gh-pages
[![Open Source Love](https://badges.frapsoft.com/os/v2/open-source.svg?v=103)](https://github.com/ellerbrock/open-source-badges/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)


The html documentation can be deployed by GitHub Pages by means
of the 'gh-pages' branch. With this action, the 'gh-pages' branch is automatically updated with the content of a specific directory.

In summary, this GitHub action does the following:

- Takes the author and SHA id of the trigger action ('push' or 'pull request') to be consistent
  along the action.
- Creates a new 'gh-pages' branch if this is not already in the repository.
- Pushes the html documentation located in a specific directory to the 'gh-pages' branch.

This GitHub Action was developed by [the Computational Biology and Drug Design Research Unit -UIBCDF- at the
Mexico City Children's Hospital Federico Gómez](https://www.uibcdf.org/). Other GitHub Actions can
be found at [the UIBCDF GitHub site](https://github.com/search?q=topic%3Agithub-actions+org%3Auibcdf&type=Repositories).

## How to use it

To include this GitHub Action, put a Yaml file (named 'html\_dir\_to\_gh\_pages.yaml', for instance) with the following content in the
directory '.github/workflows' of your repository:

```yaml
name: HTML dir to gh-pages

on:
  push:
    branches:
      - main

# workflow_dispatch:        # Un comment line if you also want to trigger action manually

jobs:
  html_dir_to_gh-pages:
    runs-on: ubuntu-latest
    name: HTML dir to gh-pages
    steps:
      - uses: actions/checkout@v2
        with:
          fetch-depth: 0
      - name: Running the HTML dir to gh-pages Action
        uses: uibcdf/action-html-dir-to-gh-pages@v1.0.0
        with:
          branch: main
          html_dir: docs/_build/html
```

### Input parameters

These are the input parameters of the action:

| Input parameters | Description | Default value | 
| ---------------- | ------------------------------------------- | ------------------------------------------------------ |
| branch | Name of the branch where the sphinx documentation is located | 'main' |
| html\_dir | Path where the html documentation is | 'docs/\_build/html' |

They are placed in the last three lines of the above workflow example file:

```yaml
      - name: Running the HTML dir to gh-pages Action
        uses: uibcdf/action-html-dir-to-gh-pages@v1.0.0
          with:
            branch: main
            html_dir: docs/_build/html
```

