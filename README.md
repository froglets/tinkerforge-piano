# tinkerforge-piano

## Tinkerforge dc-motor example using Conan C/C++ Package Manager

This repo shows how to build Tinkerforge's [C/C++ example for DC brick](https://www.tinkerforge.com/en/doc/Software/Bricks/DC_Brick_C.html#dc-brick-c-examples) using Conan C/C++ Package Manager.

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
This package includes de C/C++ API bindings from [Tinkerforge](https://www.tinkerforge.com/):

```
conan install ../conanfile.txt --build=missing
```

Configure the project and build the examples using CMake build system:

**Windows / Visual Studio**

```
cmake .. -G "Visual Studio 15" -DCMAKE_TOOLCHAIN_FILE=conan_toolchain.cmake
cmake --build . --config Release

# Run the examples:

Release/example_configuration.exe
...
Release/example_callback.exe
...
```

**Linux/macOS**

```
cmake .. -G "Unix Makefiles" -DCMAKE_TOOLCHAIN_FILE=conan_toolchain.cmake
cmake --build .

# Run the examples:

./example_configuration
...
./example_callback
...
```
