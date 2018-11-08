# CppWeb

This is a way to host your own website via a virtual environment. In this case,
the virtual environment is created using a docker container which is an
abstract representation of an operating system. This operating system
has direct access to resources via its kernel.
Therefore, the web server is running in an abstract environment, with direct
access to resources. Because the server is written in C++, it is highly efficient from a performance perspective.


## Instructions
It may be useful to start with making the Dockerfile.
This Dockerfile tells the container which instructions to
run. These instructions are necessary, since the container
will by necessity require certain packages to execute the
code that you are writing.

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

NB!
It is necessary to move your dockerfile to its own directory.
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

Voilá! Your container is up and running! 
