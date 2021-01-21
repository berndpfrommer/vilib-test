# CUDA Visual Library Test Package

This repo contains the tests from the [ViLib](https://github.com/uzh-rpg/vilib) test directory.
It demonstrates how to use ViLib in a cmake build environment.

Do not use the tests in here for anything else, they are not maintained or updated.

## How to use

Clone the repos into a source directory:
```bash
mkdir workspace
mkdir /tmp/test
cd workspace
git clone https:://github.com/uzh-rpg/vilib
git clone https:://github.com/berndpfrommer/vilib-test
```

Build the visual lib:
```bash
cd vilib/visual_lib
mkdir build
cd build
cmake -DCMAKE_INSTALL_PREFIX:PATH=/tmp/test -DCMAKE_BUILD_TYPE=Release ..
make install -j 8
```

Build the tests:
```bash
cd ../../vilib-test
mkdir build
cd build
cmake -DCMAKE_INSTALL_PREFIX:PATH=/tmp/test -DCMAKE_BUILD_TYPE=Release ..
make install -j 8
```

Download the test data files (see instructions [here](https://github.com/uzh-rpg/vilib).
Then run the tests:
```bash
./vilib_tests
```
