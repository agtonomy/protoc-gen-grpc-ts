protoc-gen-grpc
=========================
Protocol Buffers Compiler (protoc) plugin for generating grpc interfaces in TypeScript.

## Aim

This project was forked from [agreatfool/grpc_tools_node_protoc_ts](https://github.com/agreatfool/grpc_tools_node_protoc_ts), and was intended to fix an error in Window10: `%1 XXX not a valid win32 application`

* difference
  * No other tools (or npm global package) need to be installed. such as `protoc`, `grpc_tools`
  * Remove handlebar template engine. 
  * Support: Linux, OSX, Windows

## WARN 

> node-pre-gyp WARN Using needle for node-pre-gyp https download 
> node-pre-gyp ERR! install error 
> node-pre-gyp ERR! stack Error: There was a fatal problem while downloading/extracting the tarball

issue：https://github.com/mapbox/node-pre-gyp/issues/462

```bash
npm install request -g
```

## Install

```bash
npm config set unsafe-perm true
npm install protoc-gen-grpc -g
```
> If you don't want to set up a public configuration for NPM, you can try to add after the installation command `-unsafe-perm` parameters.

## How to use

```bash
# generate js codes
protoc-gen-grpc \
--js_out=import_style=commonjs,binary:./examples/src \
--grpc_out=./examples/src \
--proto_path ./examples/proto \
./examples/proto/book.proto

# generate d.ts codes
protoc-gen-grpc-ts \
--ts_out=service=true:./examples/src \
--proto_path ./examples/proto \
./examples/proto/book.proto
```
## Example

There is a complete & runnable example in folder `examples`.

Dirs:

* proto: sample proto definition
* bash: useful commands
    * build.sh: build js & d.ts codes from proto file, and tsc to build/*.js
    * server.sh: start the server
    * client.sh: start the client & send requests