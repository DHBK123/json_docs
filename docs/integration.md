---
title: Integration
---

The single required source, file `json.hpp` is in the `src` directory or [released here](https://github.com/nlohmann/json/releases). All you need to do is add

```cpp
#include "json.hpp"

// for convenience
using json = nlohmann::json;
```

to the files you want to use JSON objects. That's it. Do not forget to set the necessary switches to enable C++11 (e.g., `-std=c++11` for GCC and Clang).

The code can be compiled without C++ **runtime type identification** features; that is, you can use the `-fno-rtti` compiler flag.

[notes on exceptions](/docs/notes.html#exceptions)

## A Note on Versioning


## Package Managers

### Homebrew

If you are using OS X and [Homebrew](http://brew.sh), just type

```sh
brew tap nlohmann/json
brew install nlohmann_json
```

and you're set. If you want the bleeding edge rather than the latest release, use

```sh
brew install nlohmann_json --HEAD
```

### Meson

If you are using the [Meson Build System](http://mesonbuild.com), then you can wrap this repo as a subproject.

### Conan

If you are using [Conan](https://www.conan.io/) to manage your dependencies, merely add `jsonformoderncpp/x.y.z@vthiery/stable` to your `conanfile.py`'s requires, where `x.y.z` is the release version you want to use. Please file issues [here](https://github.com/vthiery/conan-jsonformoderncpp/issues) if you experience problems with the packages.

### Hunter

If you are using [hunter](https://github.com/ruslo/hunter/) on your project for external dependencies, then you can use the [nlohmann_json package](https://docs.hunter.sh/en/latest/packages/pkg/nlohmann_json.html). Please see the hunter project for any issues regarding the packaging.

### vcpkg

If you are using [vcpkg](https://github.com/Microsoft/vcpkg/) on your project for external dependencies, then you can use the [nlohmann-json package](https://github.com/Microsoft/vcpkg/tree/master/ports/nlohmann-json). Please see the vcpkg project for any issues regarding the packaging.

