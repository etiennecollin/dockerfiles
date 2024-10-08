# IFT3355 macOS Compiler

[![en](https://img.shields.io/badge/lang-en-red.svg)](https://github.com/etiennecollin/dockerfiles/blob/main/ift3355-macos-compilation/README.md)
[![fr](https://img.shields.io/badge/lang-fr-blue.svg)](https://github.com/etiennecollin/dockerfiles/blob/main/ift3355-macos-compilation/README_FR.md)

If you're using macOS, you will encounter a _linking_ issue when compiling the homework, even if the executable is generated. This could cause problems later in the homework.

To avoid this, I’ve created a Docker image that allows you to compile the code correctly. You just need to clone this repo and follow the instructions. Don't worry, it's literally one command in the terminal. Everything is handled by a script!

Feel free to reach out if you run into any issues. Everything works fine on my MacBook Pro M1.

## Instructions

1. Install [Docker Desktop](https://www.docker.com/products/docker-desktop/) (or just make sure Docker is working on your computer).
2. Place all the files from the `./to-install` directory at the root of the homework directory (in the same directory as `CMakeLists.txt`).
   - Replace the `CMakeLists.txt` file if your computer asks.
   - The `CMakeLists.txt` file contains only one modification: the line `set(CMAKE_TOOLCHAIN_FILE "${CMAKE_CURRENT_SOURCE_DIR}/zig-compiler/toolchain.cmake")` is added above the `project(...)` line to import the `toolchain.cmake` file.
   - This added line is only for cross-compiling the code. To run the code in the Docker container, simply comment out this line.
3. Now, to compile the project, run: `./run.sh ./build.sh` from the root of the homework.
4. Similarily, to execute the code from the container, run: `./run.sh ./build/RAY <...>` from the root of the homework.
