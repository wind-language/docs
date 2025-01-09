# Quick Start Guide

Welcome to the Wind Language Quick Start Guide! This page will walk you through the essential steps to get up and running with a "Hello World" in Wind in no time.

## Prerequisites

Before you begin, make sure you have the following:

- A **Linux** or **macOS** system.
- Basic knowledge of programming concepts.
- A terminal and a text editor.

---

## Step 1: Install Wind

To start using Wind, you need to install the compiler. Follow the steps for your operating system:

### Linux / macOS

* Open your terminal.
* Run the following command to download the Wind compiler:

```bash
   git clone https://github.com/utcq/wind
```

* Change into the `wind` directory:

```bash
   cd wind
```

* Build the compiler using CMake:

```bash
    mkdir build
    cd build
    cmake ..
    make
    cd ..
```

---

## Step 2: Write Your First Program

Once Wind is installed, create your first Wind program. Open your favorite text editor and write the following:

```wind
@include "#libc.w"

fn main(): int {
    puts("Hello, Wind!");
    return 0;
}
```

Save the file as `hello.w`.

---

## Step 3: Compile Your Program

In the terminal, navigate to the folder where you saved your program and compile it:

```bash
$(COMPILER_BUILD_DIR)/windc hello.wind -o hello
```

This will generate an executable file called `hello` in the same directory.

---

## Step 4: Run Your Program

To run your program, type:

```bash
./hello
```

You should see:

```
Hello, Wind!
```


Congratulations! You’ve just written and executed your first Wind program!

---

## Step 5: Need Help?

- [Troubleshooting](../help.md): Solutions to common issues you might face.

---

Happy coding with Wind! 🎉