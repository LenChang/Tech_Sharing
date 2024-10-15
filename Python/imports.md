# Overview

| JS | PY |
|---|--- |
| ```import * as "name" from "module_name"``` | ```import "module_name" as "name" ```
| ```import * from "module_name"``` | ```from "module_name" import *```
| ```import {"sub_module"} from "module_name"``` | ```from "module_name" import "sub_module"```

# Usage
## Standard Library

| Language | Example |
|---|---
| JS | Math.sqrt(64)
| PY | import math<br>...<br> math.sqrt(64)

## `__init__.py`
> It used to be a required part of a package (old, pre-3.3 "regular package", **not newer 3.3+** "namespace package")
- [doc](https://stackoverflow.com/questions/448271/what-is-init-py-for)

# Reference
- https://www.geeksforgeeks.org/import-module-python/
