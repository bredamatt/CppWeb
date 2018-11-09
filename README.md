# CppWeb

This is a repository used as work in progress for my company's website.
It is created with security and efficiency in mind, as the server is running inside a container.
A docker container is a abstract representation of an (or virtual) operating system. This operating system
has direct access to resources it is running on, via the virtual kernel.
Hence, running the website can be thought of as running an encapsulated service.
This encapsulation limits connectivity, rendering the service more secure. Only the port which
is exposed by the program is exposed to the network.

## Dependencies
A range of tools are used to build the website:
- C++ (http://www.cplusplus.com)
- Boost lib (https://www.boost.org)
- Docker (https://www.docker.com)
- MongoDB (https://www.mongodb.com)
- Mustache.js ()
- Crow (https://github.com/ipkn/crow)
- Mutex (https://en.cppreference.com/w/cpp/thread/mutex)
- HTML (https://www.w3schools.com/html/)
- JavaScript (https://www.javascript.com)
- WebSocket (https://html.spec.whatwg.org/multipage/web-sockets.html#network)
- cmake (https://cmake.org)
- Cascading stylesheets (CSS) (https://en.wikipedia.org/wiki/Cascading_Style_Sheets)
- AJAX (https://www.w3schools.com/php/php_ajax_intro.asp)

Additionally, the service may be deployed to Heroku easily using Heroku's Container Registry & Runtime Service.

For more information on that service, see: https://devcenter.heroku.com/articles/container-registry-and-runtime

## Structure
The structure of the repository is as follows:
```
--CppWeb
    |
    |---box (the initial container without MongoDB)
    |
    |
    |---hello_crow (main.cpp, CMakeLists.txt and Dockerfile)   <<---- main folder
    |       |
    |       |
    |       |----bbox (used to build MongoDB C and C++ Drivers for the container, has a Dockerfile)
    |       |
    |       |----build (executable folder)
    |       |
    |       |----public (.html files / views)
    |               |
    |               |----images  (.jpeg files)
    |               |
    |               |----scripts (.js scripts)
    |               |
    |               |----styles (.css files)
    |
    |
    |---root (crow_all_.h, and other .h files here)
```

## Instructions


### Making a Dockerfile
 To specify a compiler, type:

```FROM gcc:x.x.x ```

where ```x.x.x``` represents the version number of the gcc compiler. Of course, other compilers can be specified too.

To specify a command to be executed, type:

```RUN "command" ```

For example, to upgrade ```apt-get```, type:

```RUN apt-get -qq update```

and:

```RUN apt-get -qq upgrade```

**NB!**

There are two highly important things to note. First of all, we will be using ```cmake```in this project to facilitate the build process. Indeed, this is a key reason why you would be interested in hosting a C++ webserver in a container. Therefore, make sure your Dockerfile has the following specified:

``` RUN apt-get -qq install cmake```

Secondly, it is necessary to move your dockerfile to its own directory.
Hence, execute the following in your terminal:

```$ cd ~/Project-folder ```

```~/Project-folder $ mkdir box ```

```~/Project-folder $ cd box ```

```~/Project-folder $ cp ../Dockerfile ~/Project-folder/box```

Once the file is in the ```box```dir, it is time to build the container. Navigate back to the root project folder ```~/Project-folder```, and execute the following:

``` $ docker build -t box```

This builds the container and may take some time based upon the dependencies you specified in the Dockerfile (libraries, tools fetched and installed via RUN commands).

To browse the directories in the container (recall this is an OS), run:

``` docker run -ti box:latest bash```

Voilá! Your container is up and running! You can now navigate inside the container from your terminal.

## Making the Web server
In this case, we are writing the server in C++ for high performance. Here, we are using the Crow microframework. According to the benchmark, crow can handle up to 300,000 requests per second. It also contains both Middleware and Websocket support, which is neat for building more complex services.

Crow is very simple to use, just copy ```amalgamate/crow_all.h```and use it in your project by including it in your C++ webserver with:

```#include "crow_all.h" ```

For more information, see: https://github.com/ipkn/crow
