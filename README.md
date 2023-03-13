# conflupy

![GitHub Workflow Status](https://img.shields.io/github/actions/workflow/status/yoobato/conflupy/publish-to-pypi.yml)
![PyPI](https://img.shields.io/pypi/v/conflupy)

A Python library for Atlassian Confluence REST API
> Version 1.0.0, 1.1.0 is for distribution test and has bugs. Please use conflupy >= 1.2.0

## Requirements
- Python >= 3.9
- Atlassian Confluence ([REST API docs](https://docs.atlassian.com/ConfluenceServer/rest/7.19.0))
  - This library is tested in `Atlassian Confluence 7.19.0`
  - [Confluence REST API examples](https://developer.atlassian.com/server/confluence/confluence-rest-api-examples)
  - [Confluence Storage Format](https://confluence.atlassian.com/conf719/confluence-storage-format-1157466554.html)

## Installation
```sh
pip install conflupy
```

## Usage
```python
from confluence import Confluence

# Initialize Confluence
confluence = Confluence(base_url: 'https://confluence.example.com', account: (USER_ID, USER_PW))

# Get Pages
pages = confluence.get_pages(space_key='TEST')
print('Pages :', pages)

# Get Specific Page
page = confluence.get_content(content_id='1349141')
print('Page :', page)

# Create a new Page
body = '<h1>Hello</h1><br /><p>This is a page created with REST API</p>'
new_page = create_page(space_key='TEST', title='Test Page', body=body)
print('New Page :', new_page)
```

## Build & Deploy (PyPi)
```sh
# Build
pip install build
python -m build
# whl file & archived src(tar.gz) file will be generated.

# Deploy
pip install twine
python -m twine upload dist/*
# package will be uploaded to PyPi registry
# https://pypi.org/project/conflupy
```
> However, this project use GitHub Actions workflow to automatically publish the package to PyPI when a tag pushed.

## To Do
- [ ] Unittest

## Authors
- [Daeyeol Ryu](https://yoobato.com)

## License
- [Apache License 2.0](./LICENSE.md)
