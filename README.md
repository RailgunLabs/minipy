<picture>
  <source media="(prefers-color-scheme: dark)" srcset=".github/minipy-dark.svg">
  <source media="(prefers-color-scheme: light)" srcset=".github/minipy.svg">
  <img alt="Minipy" src=".github/minipy.svg" width="408px">
</picture>

**Minipy** is a minifier and obfuscator for Python source code.

[![Homepage](https://img.shields.io/badge/Homepage-blue)](https://RailgunLabs.com/minipy/)&nbsp;
[![Documentation](https://img.shields.io/badge/Documentation-blue)](https://RailgunLabs.com/minipy/manual/)

## Example

Minipy converts a string (or file) of Python source code into a more compact form, optionally substituting variables with shorter variations where possible.
Variable substitution honors imported modules regardless of whether they are 1st or 3rd party modules, e.g. it will **not** minifiy imported identifiers such as `path` or `exists` in `os.path.exists()`.

Input:

```py
import os

# Check if the JSON file exists.
def json_exists(filename: str) -> bool:
    with_ext = filename + ".json"
    return os.path.exists(with_ext)
```

Minified:

```py
import os
def json_exists(filename:str)->bool:
 with_ext=filename+".json"
 return os.path.exists(with_ext)
```

Obfuscated:

```py
import os
def a(b):
 c=b+"json
 return os.path.exists(c)
```

## Command-line Usage

Minipy can be consumed as a library or as a standalone command-line program.
Executing the following command from your shell will minify the Python file named `filename.py`.
If no file is specified, then Minipy will read from `stdin`.

```bash
$ minipy filename.py
```

Minify _and_ obfuscate with:

```bash
$ minipy --obfuscate filename.py
```

The `-s` flag suppresses obfuscation of identifiers.
This is useful for preventing public functions, classes, variables, etc. from being obfuscated.
The following command would prevent identifiers `foo` and `bar` from being obfuscated.

```bash
$ minipy --obfuscate -s foo -s bar filename.py
```

## Installation

Minipy requires Python 3.12 or newer

Install Minipy by downloading the latest version from the [releases page](https://github.com/RailgunLabs/minipy/releases/) and installing with:

```bash
$ pip install minipy-0.9.2-py3-none-any.whl
```

## Support

* [Documentation](https://RailgunLabs.com/minipy/manual/)
* [Premium Support](https://RailgunLabs.com/services/)

## License

Minipy is free for non-commercial use.

You can purchase a commercial license from [Railgun Labs](https://RailgunLabs.com/minipy/license/).
