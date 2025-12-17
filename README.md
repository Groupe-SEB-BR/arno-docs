# Arno-Doc

Documentation site built with [MkDocs](https://www.mkdocs.org/).

## Getting Started

### Prerequisites

- Python 3.7 or higher
- pip

### Installation

```bash
pip install mkdocs
```

### Running Locally

To start the development server:

```bash
mkdocs serve --livereload
```

Visit `http://127.0.0.1:8000` in your browser.

### Building the Site

To build the static site:

```bash
mkdocs build
```

The built site will be in the `site/` directory.

## Project Structure

```
arno-doc/
├── docs/           # Documentation source files
├── mkdocs.yml      # MkDocs configuration
└── site/           # Built site (generated)
```

## Configuration

Edit `mkdocs.yml` to customize:

- Site name and description
- Theme
- Navigation structure
- Plugins and extensions

## Contributing

1. Edit markdown files in the `docs/` directory
2. Test changes with `mkdocs serve`
3. Commit and push your changes

## Documentation

For more information, visit the [MkDocs documentation](https://www.mkdocs.org/).