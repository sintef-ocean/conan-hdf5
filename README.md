[![GCC Conan](https://github.com/sintef-ocean/conan-hdf5/workflows/GCC%20Conan/badge.svg)](https://github.com/sintef-ocean/conan-hdf5/actions?query=workflow%3A"GCC+Conan")
[![Clang Conan](https://github.com/sintef-ocean/conan-hdf5/workflows/Clang%20Conan/badge.svg)](https://github.com/sintef-ocean/conan-hdf5/actions?query=workflow%3A"Clang+Conan")
[![MSVC Conan](https://github.com/sintef-ocean/conan-hdf5/workflows/MSVC%20Conan/badge.svg)](https://github.com/sintef-ocean/conan-hdf5/actions?query=workflow%3A"MSVC+Conan")

[Conan.io](https://conan.io) recipe for [hdf5](https://portal.hdfgroup.org/display/HDF5/HDF5).

The package is usually consumed using the `conan install` command or a *conanfile.txt*.

## How to use this package

1. Add remote to conan's package [remotes](https://docs.conan.io/en/latest/reference/commands/misc/remote.html?highlight=remotes):

   ```bash
   $ conan remote add sintef https://artifactory.smd.sintef.no/artifactory/api/conan/conan-local
   ```

2. Using *conanfile.txt* in your project with *cmake*

   Add a [*conanfile.txt*](http://docs.conan.io/en/latest/reference/conanfile_txt.html) to your project. This file describes dependencies and your configuration of choice, e.g.:

   ```
   [requires]
   hdf5/[>=1.8.21]@sintef/stable

   [options]


   [imports]
   licenses, * -> ./licenses @ folder=True

   [generators]
   cmake_paths
   cmake_find_package
   ```

   Insert into your *CMakeLists.txt* something like the following lines:
   ```cmake
   cmake_minimum_required(VERSION 3.13)
   project(TheProject CXX)

   include(${CMAKE_BINARY_DIR}/conan_paths.cmake)
   find_package(HDF5 MODULE REQUIRED)

   add_executable(the_executor code.cpp)
   target_link_libraries(the_executor HDF5::HDF5)
   ```
   Then, do
   ```bash
   $ mkdir build && cd build
   $ conan install .. -s build_type=<build_type>
   ```
   where `<build_type>` is e.g. `Debug` or `Release`.
   You can now continue with the usual dance with cmake commands for configuration and compilation. For details on how to use conan, please consult [Conan.io docs](http://docs.conan.io/en/latest/)

## Package options

Option | Default | Domain
---|---|---
shared | False | [True, False]
fPIC | True | [True, False]
enable_cxx | True | [True, False]
hl | True | [True, False]
threadsafe | True | [True, False]
with_zlib | True | [True, False]
szip_support | None | [None, "with_libaec", "with_szip"]
szip_encoding | False | [True, False]
allow_unsupported | True | [True, False]

## Known recipe issues

(Add known issues/shortcomings here)
