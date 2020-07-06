# Bulding packages

This repository contains necessary tools to automate building packages for various platforms all at once. There is one package "project" per directory completely self contained with all of the following:
  - Top level 'build_all' script
  - List of platforms to build for
  - Fallback GPG public and private keys
  - Subfolders each describing one platform
    - Platform build script
    - Dockerfile for build image
    - Inside docker build script
    - Dockerfile for test image
    - Inside dokcer test script

### The technology
Package building is based on `fpm-within-docker` developed by [Alan Franzoni](https://github.com/alanfranz/fpm-within-docker). Start by copying example project from [upstream repo](https://github.com/alanfranz/fpm-within-docker) and altering it to your needs.

### Usual workflow
 1) Have platform docker image ready (AmazonLinux, AmazonLinux2, OracleLinux7, etc) - see upstream repo for pre-baked ones
 2) Have FWD docker image ready (Platform + FPM)
 3) Update build_all script as required
     - Downloading and unpacking source code
     - Generating env.list file with variables to pass to docker
     - Launching build script for each platform
     - Moving output packages to a common folder
