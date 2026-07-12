# Linksaver (`l2`)

## Link and Dependency Documentation Tool

**Linksaver** is a CLI tool for saving, organizing and documenting links, licenses, dependencies and external resources used by software projects.

The command line executable is called:

```bash
l2
```

Linksaver creates a structured `linksaver.json` file and can generate human-readable documentation files in Markdown and TXT format.

---

# Features

Linksaver helps developers to keep track of:

* Project links
* External resources
* Authors and licenses
* License files
* Package dependencies
* Cargo dependencies
* Git submodules
* Change notices
* Project documentation

Generated documentation can be used for:

* Open source projects
* License compliance
* Credits pages
* Documentation websites
* Dependency reports

---

# Installation

## From source

Clone the repository:

```bash
git clone https://github.com/ShadowDara/linksaver2
```

Run:

```bash
python linksaver.py
```

To install the CLI command:

```bash
pip install .
```

After installation:

```bash
l2 help
```

should work globally.

---

# Quick Start

Initialize Linksaver inside your project:

```bash
l2 init
```

Example:

```
Init Linksaver

Projectname: MyProject

Created config at linksaver.json
```

This creates:

```
your-project/
│
├── linksaver.json
└── .samengine/
    ├── links.info.md
    └── links.info.txt
```

---

# Commands

## Help

Show all available commands:

```bash
l2 help
```

Output:

```
help
init
add
add2
add3
view
viewx
list
addpkg
addcargo
open
addsubmodule
clonesubm
```

---

# Project Initialization

## `init`

Creates a new Linksaver configuration.

Usage:

```bash
l2 init
```

Creates:

```json
{
    "projectname": "Example",
    "links": []
}
```

---

# Adding Links

## `add`

Adds a normal link entry.

Usage:

```bash
l2 add
```

Example:

```
Name (optional): wxWidgets
Author (optional): wxWidgets Team
License (optional): LGPL
License Link: https://www.wxwidgets.org/about/licence/

New Link:
https://github.com/wxWidgets/wxWidgets

New Description:
Cross-platform GUI library
```

Result:

```json
{
    "name": "wxWidgets",
    "link": "https://github.com/wxWidgets/wxWidgets",
    "description": "Cross-platform GUI library",
    "license": "LGPL"
}
```

---

# Adding Text Entries

## `add2`

Adds a simple text entry.

Usage:

```bash
l2 add2
```

Example:

```
Entry text:
Uses SDL2 for rendering
```

---

# Adding License Files

## `add3`

Adds a license file reference.

Usage:

```bash
l2 add3
```

Example:

```
License file:
thirdparty/library/LICENSE
```

During Markdown/TXT generation the file content is included.

---

# Generate Documentation

## Markdown output

Command:

```bash
l2 view
```

Creates:

```
.samengine/links.md
```

Example output:

```markdown
# Links for MyProject

Used for MyProject:

- **wxWidgets**
  (https://github.com/wxWidgets/wxWidgets)
  - Cross platform GUI library
  - licensed under LGPL
```

---

## TXT output

Command:

```bash
l2 viewx
```

Creates:

```
.samengine/links.txt
```

Useful for:

* Plain text credits
* License archives
* Automated processing

---

# Listing Credits

## `list`

Displays saved links directly in the terminal.

Usage:

```bash
l2 list
```

Example:

```
"wxWidgets"
https://github.com/wxWidgets/wxWidgets

by wxWidgets Team

licensed under LGPL
```

---

# Opening Links

## `open`

Opens all saved links in the default browser.

Usage:

```bash
l2 open
```

Supported systems:

* Windows
* Linux
* macOS

---

# Package Lock Support

## Import npm dependencies

Command:

```bash
l2 addpkg
```

Reads:

```
package-lock.json
```

and extracts:

* Package name
* Version
* License
* npm link
* Date

Example:

```json
{
    "name": "react",
    "version": "18.0.0",
    "license": "MIT"
}
```

Requires:

```
node_modules/
package-lock.json
```

---

# Cargo Support

## Import Rust dependencies

Command:

```bash
l2 addcargo
```

Reads:

```
Cargo.lock
```

and searches:

```
~/.cargo/registry/src
```

Extracts:

* Crate name
* Version
* License
* crates.io URL

Example:

```json
{
    "name": "serde",
    "version": "1.0",
    "license": "MIT OR Apache-2.0"
}
```

Requires:

```bash
cargo fetch
```

---

# Git Submodules

Linksaver can save and clone external Git repositories.

## Add a submodule entry

Command:

```bash
l2 addsubmodule
```

Example:

```
Description:
wxWidgets source

Directory:
thirdparty

Clone directory:
wxWidgets

Repository:
https://github.com/wxWidgets/wxWidgets

Commit:
670835aec7e54b9e9d5a50d6a1aea1e8ba0bcdb2
```

Stored as:

```json
{
    "git": {
        "submodules": [
            {
                "desc": "wxWidgets source",
                "dir": "thirdparty",
                "clonedir": "wxWidgets",
                "repolink": "...",
                "repocommit": "..."
            }
        ]
    }
}
```

---

## Clone submodules

Command:

```bash
l2 clonesubm
```

Linksaver will:

1. Create the target directory
2. Clone the repository
3. Checkout the requested commit
4. Initialize Git submodules

Example:

```
Cloning dependencies

wxWidgets source

Cloned wxWidgets successfully!

Finished cloning every submodule!
```

---

# Configuration File

The main configuration file:

```
linksaver.json
```

Example:

```json
{
    "projectname": "MyProject",

    "pretty": true,

    "links": [],

    "links2": [],

    "links3": [],

    "links4": [],

    "links5": [],

    "linkspkglock": [],

    "linkscargolock": [],

    "settings": {
        "selectmenu": false
    },

    "git": {
        "submodules": []
    }
}
```

---

# Interactive Menu

Linksaver also supports a menu mode.

Enable:

```json
{
    "settings": {
        "selectmenu": true
    }
}
```

Run:

```bash
l2
```

Example:

```
=== Linksaver ===

1. Open all links
2. Init
3. Add link
4. Add text entry
5. Add license file
6. Generate Markdown
7. Generate TXT
8. List credits
9. Import package-lock.json
10. Import Cargo.lock
11. Help
12. Add Git Submodule
13. Clone git submodules
14. Exit
```

---

# Generated Files

After using `view`:

```
.samengine/
│
├── links.md
├── links.txt
├── links.info.md
└── links.info.txt
```

---

# Supported Platforms

Linksaver supports:

* Windows
* Linux
* macOS

---

# Development

Written in:

```
Python
```

Main technologies:

* Dataclasses
* JSON serialization
* pathlib
* subprocess
* Git integration

---

# License

Linksaver is licensed under:

```
Apache License 2.0
```

Copyright:

```
ShadowDara 2026
```

Do not remove the license notice from the source code.

---

# Author

Created by:

**ShadowDara**

Project documentation:

```
https://shadowdara.github.io/docs/#/linksaver
```

---

# Version

Current version:

```
3.0.0
```

*EDIT DATE: 12.07.2026*
