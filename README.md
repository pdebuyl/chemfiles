# Chemharp, an efficient IO library for chemistry file formats

Chemharp is a modern C++ library for reading and writing from and to trajectory
files. These files are created by your favorite program, and contains informations
about atomic or residues names and positions. Some format also have additional
informations, such as velocities, forces, energy, masses, charges, …

The main targeted audience of Chemharp (libchemharp) is chemistry researcher
working on their own code to do some kind of awesome science, without bothering
about handling all the format that may exist in the world.

Running simulation (either minimisations, Monte Carlo or Molecular Dynamic) often
require a two-step process: running the simulation and writing data to a file,
and then using some analysis tool on that data. Chemharp try to help you for the
second point.

## Features

 - Automatic recognition of file type based on filename extension;
 - Open-source under the Mozilla Public License;
 - Cross platform: Windows, Linux, Mac OS X, maybe others;
 - Support for a number of atoms which is not constant.

## Planned Features

 - Bindings to the most used scientific languages:  Python, Julia, C, Fortran 95
 - Binding to even more languages: Lua, Java, ...
 - More formats !
 - More speed !
 - Support for very big files, over network.

## File formats

### Supported formats

| Format        | Read ? | Write ? |
| ------------- | ------ | ------- |
| XYZ           | yes    |  yes    |

### Planned formats

See the [issue list](https://github.com/Luthaf/Chemharp/labels/New%20Format) for
planned formats. If you want a new format to be added to Chemharp, you can either
do it by yourself (it is easy !) and create a pull-request to incorporate your
changes, or create a new issue with a link to the format reference and some
example of well-formed files.

## Getting started

### Getting the code, building, installing

To get the code, please use `git`
```bash
git clone --recursive https://github.com/Luthaf/Chemharp
cd Chemharp
```

Then, [`cmake`](http://cmake.org/) is used to build the code. It should be
available in your favorite package manager. So, create a folder and go for the
build:
```bash
mkdir build
cd build
cmake ..
```

You can also configure the build at command line. The mains options are `-DBUILD_TESTS=ON` to build the tests suite, and `-DBUILD_DOCUMENTATION` to build a local copy of the documentation.

Then, you can build and install the library by running the following commands:
```bash
make
make install
```

### Testing the code

You may want to run the tests before installing. To do so, use the `ctest` command:
```bash
ctest # or ctest -jn to run n parallel processes
```

All tests should pass, if they don't please fill an [issue](https://github.com/Luthaf/Chemharp/issues).

### Usage

C++ API:
```c++

```

C API:
```c
HARP_FILE *file = harp_open("filename.xyz");

harp_close(file);
```

TODO: add a link to the doc

## Why not OpenBabel ?

Hard question … OpenBabel is a pretty big and good piece of software. I just
didn't find in this project what I was looking for: a simple abstraction on the
top of chemistry file formats to allow me, *as a programmer*, to write my own
code without thinking about IO. OpenBabel is mainly made for conversions from a
file format to an other, and not for analysis.

Moreover, OpenBabel is GPL software, which might make it harder to use by
other softwares. For that point, MPL is (in my own opinion) a good compromise:
you have to publish the files you modified under MPL, but you can use whatever
licence you want for the rest of your code.

But maybe I am just reinventing the squared wheel =)

## Licence

All this code is copyrighted by Guillaume Fraux, and put to your disposition
under the termes of the Mozilla Public Licence v2.0.
