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

**Notes**
-The linear potentiometer controls volume. 0 is the lowest volume. 100 effevtively mutes the beeper.
-Piano keys are on two pieces of standard 8.5" x 11" printer paper.
-Piano keys start 10mm from the IR sensors. They are 40mm wide, 2" tall, and 1" from the edge of the paper.
-The IR sensors seem to have trouble beyond 600mm. Their maxiumum range is 800mm. The backstop is meant to ensure more reliable measurements. It's a few inches away from the edge of the second paper.
-Hovering a finger above key that's close to the sensor is detected the same as placing your hand on a key that's farther away.
