# Quick Start Guide

Welcome to the Wind Language Quick Start Guide! This page will walk you through the essential steps to get up and running with a "Hello World" in Wind in no time.

## Prerequisites

Before you begin, make sure you have the following:

- A **Linux** or **macOS** system.
- Basic knowledge of programming concepts.
- A terminal and a text editor.

---

## Step 1: Write Your First Program

Once Wind is installed, create your first Wind program. Open your favorite text editor and write the following:

```wind
@include "#libc.w"

func main(): int {
    puts("Hello, Wind!");
    return 0;
}
```

Save the file as `hello.w`.

---

## Step 2: Compile Your Program

In the terminal, navigate to the folder where you saved your program and compile it:

```bash
windc hello.wind -o hello
```

This will generate an executable file called `hello` in the same directory.

---

## Step 3: Run Your Program

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

## Step 4: Need Help?

- [Syntax](./syntax.md): Learn more about the syntax of Wind.
- [Troubleshooting](../help.md): Solutions to common issues you might face.

---

Happy coding with Wind! 🎉