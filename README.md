# Super Mario War

## About

Super Mario War is a Super Mario multiplayer game.
The goal is to stomp as many other Marios as possible to win the game.
It's a tribute to Nintendo and the game Mario War by Samuele Poletto.

The game uses artwork and sounds from Nintendo games. We hope that this noncommercial fangame qualifies as fair use work. We just wanted to create this game to show how much we adore Nintendo's characters and games.

### Features

- Up to four players deathmatch fun
- a whole bunch of game modes (featuring GetTheChicken, Domination, CTF, ...)
- online and local multiplayer
- Comes with the leveleditor - you can create your own maps...
- ... and a lot of people did so. There are currently over 1000 maps
- More fun than poking a monkey with a stick
- The whole source code of the game is available, for free
- uses SDL and is fully portable to windows, linux, mac, ...
- CPU Players
- will make you happy and gives you a fuzzy feeling

### Supported platforms

- Linux
- Windows
- XBox (?)
- Mac OS X (?)
- asm.js

## Building instructions

### Requirements

- cmake
- SDL 1.2 or 2.0, with
    - SDL_image
    - SDL_mixer
- ENet (optional)

On Linux, this usually means the following packages: `cmake libsdl1.2-dev libsdl-image1.2-dev libsdl-mixer1.2-dev libenet-dev`

For other systems, you can download the development files manually from:

- http://www.cmake.org/cmake/resources/software.html#latest
- http://www.libsdl.org/download-1.2.php
- http://www.libsdl.org/projects/SDL_image/release-1.2.html
- http://www.libsdl.org/projects/SDL_mixer/release-1.2.html
- http://enet.bespin.org/Downloads.html

### Linux

Enter the build directory, run cmake, then make and finally you can use the binary smw in Build/Binaries directories.

```sh
$ mkdir Build
$ cd Build && cmake .. && make -j5
$ Binaries/smw ../data_full
```

If you have troubles at compiling you might want to use instead:

```sh
$ VERBOSE=1 make -j5
```

To compile with debugging symbols, enable the relative option:

```sh
$ cd Build && cmake -DDEBUG=ON .. && make -j5
$ gdb Binaries/smw
gdb> run ../data
```

### Windows

Note: You can use MinGW and MinGW Shell/Cygwin for compiling too.

Visual Studio:

- make sure you have CMake in your PATH
- go to Build directory and issue `cmake ..`
- open the generated solution smw.sln, right-click on the smw project and go to Configuration Properties -> C/C++ - Command line and remove everything there
- on the same group, go to Linker and add your lib directory there
- change also system to WINDOWS (not console)
- now it will compile and smw.exe can be found in build\Binaries\Debug\smw.exe. make sure you copy the necessary SDL dlls along with smw.exe, otherwise it won't work

### ASM.JS

SMW can be build to run in your browser. For this, you need
emscripten with the special LLVM backend, and clang.
See [here](https://github.com/kripken/emscripten/wiki/LLVM-Backend) for more information.

You can prepare a build directory with the following commands:

```sh
$ mkdir build-js && cd build-js
$ ln -s ../data data
$ emconfigure cmake .. -DUSE_EMSCRIPTEN=1
```

Then build with:

```sh
$ emmake make
$ emcc Binaries/smw.bc -o smw.html -O3 -v --preload-file data -s OUTLINING_LIMIT=60000 -s ALLOW_MEMORY_GROWTH=1
$ emcc Binaries/leveledit.bc -o leveledit.html -O3 -v --preload-file data -s OUTLINING_LIMIT=60000 -s ALLOW_MEMORY_GROWTH=1
$ emcc Binaries/worldedit.bc -o worldedit.html -O3 -v --preload-file data -s OUTLINING_LIMIT=60000 -s ALLOW_MEMORY_GROWTH=1
```

### Compilation options

To set build options you can use `cmake-gui`.
Alternatively, open CMakeLists.txt to see what options are available, they are described on the beginning the file.

## How to play

Please see documentation in docs/ directory.
