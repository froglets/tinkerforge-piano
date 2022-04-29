# tinkerforge-piano
This repo houses the code used to build a Tinkerforge piano using Conan C/C++ Package Manager.

### Requirements

Needed tools installed in your machine to run the examples:

- Python with `pip` package manager installed
- Conan: `pip install Conan` or download from https://conan.io/downloads
- CMake: https://cmake.org/download
- Compiler of choice: gcc, clang, apple-clang, visual studio

### Building the examples

Create a `build` directory and change to it:

```
mkdir build && cd build
```

Install `tinkerforge-bindings/2.1.32` package from [ConanCenter](https://conan.io/center/tinkerforge-bindings).
This package includes C/C++ API bindings from [Tinkerforge](https://www.tinkerforge.com/):

```
conan install ../conanfile.txt --build=missing
```

Configure the project and build the examples using CMake build system:

**Windows / Visual Studio**

```
cmake .. -G "Visual Studio 16" -DCMAKE_TOOLCHAIN_FILE="conan_toolchain.cmake"
cmake --build . --config Release
./Release/tinkerforgePiano
```

**Linux/macOS**

```
cmake .. -G "Unix Makefiles" -DCMAKE_TOOLCHAIN_FILE=conan_toolchain.cmake
cmake --build .
./tinkerforgePiano
```
