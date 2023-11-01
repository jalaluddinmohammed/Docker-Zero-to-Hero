# Without Multi Stage Docker Build

On a single stage we download Ubuntu or Centos or any other image, we install all dependencies, build it and sometimes the image size would go up to 1 to 1.5 GB.

This much heavy image size has a security threat as it has many os related packages on it.

To reduce the image size, security threat, we need to follow multi stage docker build with distoreless images.

First stage, is we build the image with ubuntu,centos operating system, but we dont execute the binary.

We exectue that in a second stage using distroless image which reduces the size as it will just have run time software, like python, jdk or incase of go lang it just scratch & a binary which we copied
from stage 1 build phase.




# Multi Stage Docker Build

The main purpose of choosing a golang based applciation to demostrate this example is golang is a statically-typed programming language that does not require a runtime in the traditional sense. Unlike dynamically-typed languages like Python, Ruby, and JavaScript, which rely on a runtime environment to execute their code, Go compiles directly to machine code, which can then be executed directly by the operating system.

So the real advantage of multi stage docker build and distro less images can be understand with a drastic decrease in the Image size.


# Distroless images

https://github.com/GoogleContainerTools/distroless
