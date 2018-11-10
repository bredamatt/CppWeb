# CppWeb

This is a repository used as work in progress for my company's website. It is created with security and performance in mind, as the C++ server is running inside a Docker container.

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

### Usage
To test this simply execute the following commands from your terminal:

```$ git clone ```

Navigate to the /hello_crow dir and execute (remember the . ):

```$ docker build --rm --squash --no-cache -t hello_crow:latest . ```

Follow the instructions on https://devcenter.heroku.com/articles/container-registry-and-runtime to deploy your container to Heroku.

Navigate to localhost:8080 in Chrome, then use the route handlers as specified in main.cpp to test the service. You should be able to:

1. View contacts in JSON
2. View contacts in formatted JSON (AJAX Bulma)
3. Enter a chat room
4. Query a specific contact
5. Adding doubles, integers, or strings
6. Accessing an about page

Try to look these up in ```main.cpp```

## Using Crow
In this case, we are writing the server in C++ for high performance. Here, we are using the Crow microframework. According to the benchmark, crow can handle up to 300,000 requests per second. It also contains both Middleware and Websocket support, which is neat for building more complex services.

Crow is very simple to use, just copy ```amalgamate/crow_all.h```and use it in your project by including it in your C++ webserver with:

```#include "crow_all.h" ```

For more information, see: https://github.com/ipkn/crow
