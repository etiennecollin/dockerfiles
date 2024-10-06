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
   - The `CMakeLists.txt` file contains only one modification: the line `set(CMAKE_TOOLCHAIN_FILE "${CMAKE_CURRENT_SOURCE_DIR}/toolchain.cmake")` is added above the `project(...)` line to import the `toolchain.cmake` file.
3. Now, to compile the project, run: `docker compose run ift3355 ./build.sh` from the root of the homework.

You can create an **alias** for this long command. To do this, add the following line to your `~/.bashrc` and/or `~/.zshrc` files:

```bash
alias ift3355="docker compose run ift3355 ./build.sh"
```

After restarting your terminal, you’ll be able to simply use the `ift3355` command from the root of the homework to compile your code.
