# Multi-File

- [Multi-File](#multi-file)
  - [Objectives](#objectives)
  - [Introduction](#introduction)
  - [Multi-File Programming in C++](#multi-file-programming-in-c)
    - [Header Files and Source Files](#header-files-and-source-files)
    - [Makefile and Build Systems](#makefile-and-build-systems)
  - [Links and Resources](#links-and-resources)

## Objectives

- Understand the concept of multi-file projects
- Understand the concept of modular programming
- Understand the concept of file organization
- Understand the concept of file linking
- Understand the concept of file importing
- Understand the concept of multi-file programming in C++
- Understand the concept of makefile and build systems

## Introduction

A multi-file project is a project that consists of multiple files. This is a common practice in software development, as it allows for better organization, easier maintenance, and more efficient collaboration. In a multi-file project, each file is responsible for a specific part of the program. This is known as modular programming, and it allows for better code reusability and easier debugging.

In a multi-file project, files are organized in a way that makes it easy to find and understand the code. This usually involves grouping related files together in directories, and using a consistent naming convention for files and directories. Files are linked together using various methods, such as `#include` in C++ or `import` in Python. This allows the code in one file to use the code in another file.

Some examples of a good file organization example for a music player project is shown below:

```plaintext
music_player/
    ├── src/
    │   ├── main.cpp
    │   ├── audio_player.cpp
    │   ├── audio_player.hpp
    │   ├── playlist.cpp
    │   ├── playlist.hpp
    │   ├── song.cpp
    │   └── song.hpp
    └── Makefile
```

```plaintext
music_player/
    ├── src/
    │   ├── audio_player/
    │   │   ├── audio_player.cpp
    │   │   └── audio_player.hpp
    │   ├── playlist/
    │   │   ├── playlist.cpp
    │   │   └── playlist.hpp
    │   ├── song/
    │   │   ├── song.cpp
    │   │   └── song.hpp
    │   └── main.cpp
    └── Makefile
```

In the first example, all the source files are placed in the `src` directory. In the second example, the source files are further organized into subdirectories based on their functionality. Both examples are valid, and the choice of organization depends on the specific requirements of the project. The important thing is to have a consistent and logical organization that makes it easy to find and understand the code. There are many other ways to organize files in a multi-file project, and the best approach depends on the specific requirements of the project, these two examples are just a few of them.

## Multi-File Programming in C++

### Header Files and Source Files

In C++, multi-file programming is done using header files and source files. Header files contain declarations of functions and classes, while source files contain the definitions of these functions and classes. The header files are included in the source files using the `#include` directive. This allows the source files to use the functions and classes declared in the header files.

For example, consider the following header file `myclass.hpp`:

```cpp
#ifndef MYCLASS_H
#define MYCLASS_H

class MyClass {
public:
    void myFunction();
};

#endif
```

And the following source file `myclass.cpp`:

```cpp
#include "myclass.hpp"

void MyClass::myFunction() {
    // function definition
}
```

The `myclass.cpp` file contains the definition of the `MyClass` class and its `myFunction` method. The `myclass.hpp` file contains the declaration of the `MyClass` class. The `#include` directive in `myclass.cpp` allows the code in `myclass.cpp` to use the code in `myclass.hpp`.

Header files usually contain include guards to prevent multiple inclusions of the same file. This is done using preprocessor directives, as shown in the example above. The `#ifndef`, `#define`, and `#endif` directives are used to create an include guard. This ensures that the header file is only included once in each source file.

By using `#include` directives and include guards, the code in the header files can be used in multiple source files without causing any issues.

### Makefile and Build Systems

In a multi-file project, it is important to have a build system that can compile and link the files together. This is usually done using a makefile, which contains instructions for compiling and linking the files. The makefile specifies the dependencies between the files, and the commands to compile and link the files. This allows for easy compilation and linking of the files, and ensures that the project is built correctly.

A simple makefile for a C++ project might look like this:

```makefile
CXX = g++
CXXFLAGS = -std=c++11 -Wall

SRCS = main.cpp audio_player.cpp playlist.cpp song.cpp
OBJS = $(SRCS:.cpp=.o)
EXEC = music_player

all: $(EXEC)

$(EXEC): $(OBJS)
    $(CXX) $(CXXFLAGS) -o $@ $(OBJS)

%.o: %.cpp
    $(CXX) $(CXXFLAGS) -c $< -o $@

clean:
    rm -f $(OBJS) $(EXEC)
```

In this makefile, the `CXX` variable specifies the C++ compiler to be used, and the `CXXFLAGS` variable specifies the compiler flags. The `SRCS` variable contains the list of source files, and the `OBJS` variable contains the list of object files. The `EXEC` variable contains the name of the executable file to be generated. The `all` target specifies that the `music_player` executable should be built. The `$(EXEC): $(OBJS)` line specifies the dependencies between the executable and the object files, and the command to link the object files into the executable. The `%.o: %.cpp` line specifies the dependencies between the source files and the object files, and the command to compile the source files into object files. The `clean` target specifies the command to remove the object files and the executable. This makefile can be used to compile and link the files in the `music_player` project. The `make` command can be used to build the project, and the `make clean` command can be used to clean up the project.

another (simpler) example of a makefile for a C++ project might look like this:

```makefile
CXX = g++
CXXFLAGS = -std=c++11 -Wall

all: music_player

music_player: main.o audio_player.o playlist.o song.o
    $(CXX) $(CXXFLAGS) main.o audio_player.o playlist.o song.o -o music_player

main.o: main.cpp audio_player.hpp playlist.hpp song.hpp
    $(CXX) $(CXXFLAGS) -c main.cpp -o main.o

playlist.o: playlist.cpp playlist.hpp song.hpp audio_player.hpp
    $(CXX) $(CXXFLAGS) -c playlist.cpp -o playlist.o

audio_player.o: audio_player.cpp audio_player.hpp song.hpp
    $(CXX) $(CXXFLAGS) -c audio_player.cpp -o audio_player.o

song.o: song.cpp song.hpp
    $(CXX) $(CXXFLAGS) -c song.cpp -o song.o

clean:
    rm -f music_player *.o
```

In this makefile, the `CXX` variable specifies the C++ compiler to be used, and the `CXXFLAGS` variable specifies the compiler flags. The `all` target specifies that the `music_player` executable should be built. The `music_player: main.o audio_player.o playlist.o song.o` line specifies the dependencies between the executable and the object files, and the command to link the object files into the executable. The `main.o: main.cpp audio_player.hpp playlist.hpp song.hpp` line specifies the dependencies between the source files and the object files, and the command to compile the source files into object files. The `clean` target specifies the command to remove the object files and the executable. This makefile can be used to compile and link the files in the `music_player` project. The `make` command can be used to build the project, and the `make clean` command can be used to clean up the project.

There are other build systems that can be used to compile and link multi-file projects, such as CMake, SCons, and Autotools. The choice of build system depends on the specific requirements of the project, and the familiarity of the developers with the build system.

## Links and Resources

- [Makefile Tutorial](https://makefiletutorial.com/)
- [C++ Tutorial - Multi-File Programming](https://www.youtube.com/watch?v=9OvKEkGmvos)
- TA Multi-File Programming in C++ Workshop - Video Archive (2022)
  - [Part 1](https://www.aparat.com/v/9Ocok)
  - [Part 2](https://www.aparat.com/v/1b5yE)
- TA Multi-File Programming in C++ Workshop - Video Archive (2020)
  - [Part 1](https://www.aparat.com/v/tCL2M)
  - [Part 2](https://www.aparat.com/v/WK8Sj)
  - [Part 3](https://www.aparat.com/v/GlIL5)
- [TA Multi-File Programming in C++ Workshop](./Assets/Multi-File%20Projects%20Makefile.pdf)
- [C Plus One Magazine - Compilation Steps, Make & CMake](./Assets/Compilation%20Steps,%20Make%20&%20CMake.pdf)
