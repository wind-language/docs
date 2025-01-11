# Compiler installation Guide

Welcome to the Wind Language Installation Guide! This page will walk you through the essential steps to install the Wind compiler on your system.

## Prerequisites

Currently the Wind compiler is only supported on **Linux** and **macOS** systems. Before you begin, make sure you have the following:
 
 1. Basic knowledge of programming concepts.
 2. A terminal and a text editor.

---

## Installer Script

```bash
curl -L https://wind-lang.me/setup.sh | bash
```

---

## Compiling from source

* Open your terminal.
* Clone the Wind repository:
```bash
git clone https://github.com/utcq/wind
cd wind
```

* Build the compiler using CMake:
```bash
mkdir build && cd build
cmake ..
make
```

Now the wind compiler is installed in build/bin directory as `windc`.

Make sure to keep the source intact for the compiler to work properly.

Currently wind does not have an installer so the runtime libraries are expected to be in the source directory.

