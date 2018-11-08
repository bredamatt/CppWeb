# CppWeb

This is a way to host your own website via a virtual environment. In this case,
the virtual environment is created using a docker container which is an
abstract representation of an operating system. This operating system
has direct access to resources via its kernel.
Therefore, the web server is running in an abstract environment, with direct
access to resources. Because the server is written in C++, it is highly efficient from a performance perspective.


### Instructions
It may be useful to start with making the Dockerfile.
This Dockerfile tells the container which instructions to
run. These instructions are necessary, since the container
will by necessity require certain packages to execute the
code that you are writing.

 To specify a compiler, type:

```FROM gcc:x.x.x ```

where ```x.x.x``` represents the version number of the gcc compiler. Of course, other compilers can be specified too.

To specify a command to be executed, type:

```RUN "command" ```

For example, to upgrade ```apt-get```, type:

```RUN apt-get -qq update```

and:

```RUN apt-get -qq upgrade```
