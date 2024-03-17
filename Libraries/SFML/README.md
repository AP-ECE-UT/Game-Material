# SFML

- [SFML](#sfml)
  - [Introduction](#introduction)
  - [Installation](#installation)
  - [How to use SFML in your project](#how-to-use-sfml-in-your-project)
  - [Links and Resources](#links-and-resources)

## Introduction

SFML (Simple and Fast Multimedia Library) is a cross-platform software development library designed to provide a simple interface to various multimedia components in computers. It is written in C++ and has bindings for various other languages, including C, .Net, Python, Ruby, and D. It is designed to be easy to use and has a simple and intuitive API. It is also designed to be fast and efficient, and is optimized for performance.

SFML provides a wide range of features, including graphics, audio, networking, and windowing. It is designed to be easy to use and has a simple and intuitive API. It is also designed to be fast and efficient, and is optimized for performance.

SFML is a popular choice for game development, as it provides a wide range of features that are useful for game development, including graphics, audio, networking, and windowing. It is also designed to be easy to use and has a simple and intuitive API. It is also designed to be fast and efficient, and is optimized for performance.

## Installation

In linux, you can install the library using the following command:

```bash
sudo apt-get install libsfml-dev
```

In macOS, you can install the library using the following command:

```bash
brew install sfml
```

In Windows, you can download the pre-built binaries from the official website and install them using the installer.

## How to use SFML in your project

To use SFML in your project, you need to link the SFML libraries to your project. You can do this by adding the following lines to your project's makefile:

```makefile
LIBS = -lsfml-graphics -lsfml-window -lsfml-system
```

You also need to include the SFML headers in your source files. You can do this by adding the following line to your source files:

```cpp
#include <SFML/Graphics.hpp>
#include <SFML/Window.hpp>
#include <SFML/System.hpp>
```

Once you have linked the SFML libraries and included the SFML headers in your source files, you can use the SFML API to create windows, draw graphics, play audio, and perform other multimedia tasks. A simple example of using SFML to create a window and draw a circle is shown below:

```cpp
#include <SFML/Graphics.hpp>
#include <SFML/Window.hpp>
#include <SFML/System.hpp>

int main()
{
    sf::RenderWindow window(sf::VideoMode(800, 600), "SFML Window");

    sf::CircleShape circle(100);
    circle.setFillColor(sf::Color::Red);
    circle.setPosition(300, 200);

    while (window.isOpen())
    {
        sf::Event event;
        while (window.pollEvent(event))
        {
            if (event.type == sf::Event::Closed)
                window.close();
        }

        window.clear();
        window.draw(circle);
        window.display();
    }

    return 0;
}
```

In this example, we create a window using the `sf::RenderWindow` class, and draw a red circle using the `sf::CircleShape` class. We then enter a loop that polls for events and draws the circle on the window. When the window is closed, the program exits.

## Links and Resources

- [SFML Official Website](https://www.sfml-dev.org/tutorials/2.6/)
- [Demo Projects](./Demo/)
- [TA SFML Workshop](https://www.aparat.com/v/HKoV9)
