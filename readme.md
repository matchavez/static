# STEPS

---

1. Create repo on GitHub
2. Create readme, validate push
3. `git clone https://github.com/squidfunk/mkdocs-material.git`
4. `pip install -r mkdocs-material/requirements.txt`
5. `mkdocs new .`
6. (fence)

```sh
theme:
  name: null
  custom_dir: mkdocs-material/material

  # 404 page
  static_templates:
    - 404.html

  # Necessary for search to work properly
  include_search_page: false
  search_index_only: true

  # Default values, taken from mkdocs_theme.yml
  language: en
  font:
    text: Roboto
    code: Roboto Mono
  favicon: assets/favicon.png
  icon:
    logo: logo
  
  ```

  7. Create `.github/workflows/ci.yml`
```sh
name: ci
on:
  push:
    branches:
      - master
jobs:
  deploy:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v2
      - uses: actions/setup-python@v2
        with:
          python-version: 3.x
      - run: pip install mkdocs-material
      - run: mkdocs gh-deploy --force
```
