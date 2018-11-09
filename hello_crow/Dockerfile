FROM bbox:latest

WORKDIR /usr/src/CppWeb/hello_crow
COPY . .

WORKDIR /usr/src/CppWeb/hello_crow/build
RUN cmake .
RUN make
CMD ["./hello_crow"]
