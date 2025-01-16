# Wind syntax reference

Welcome to the Wind Language Syntax Reference! This page will guide you through the syntax of the Wind programming language, including its keywords, operators, and conventions.

---

## Comments

Comments in Wind are similar to C-style comments and can be single-line or multi-line.

```wind
// This is a single-line comment
/* This is a
   multi-line comment */
```

---

# @ Directives

Let's break the ice with the `@` directives. These are used to include files, define flags, and more.

---

### include

The `include` directive is used to include a file in the current file. The file path is relative to the current file.

```wind
@include "path/to/file.w"
```

Using # as the first character of the file path will include a file from the standard library.

```wind
@include "#types.w"
```

Multi include is also supported.

```wind
@include [
   "path/to/file1.w"
   "path/to/file2.w"
]
```

---

### import

Pay attention to the `import` directive.

```wind
@import "#my_module"
```

You can use # prefix here as well to include a module from the `WIND_PKGS_PATH`.
Import searches for a dir like this:

```yml
name/
   name.wi
   name.w
```

The `name.wi` file is the interface file, and the `name.w` file is the implementation file.
The interface file should contain the function prototypes, and the implementation file should contain the function definitions.

Interface file example:
```wind
func test_fn(x: int): int;
```

Implementation file example:
```wind
func test_fn(x: int): int {
   return x*(x+1);
}
```

---


### pure

The `pure` directive is used to define a function flag.

```wind
@pure[stack expr] func foo() {}
```

 - `stack` - Local variables usage won't be optimized.
 - `expr` - Expressions aren't optimized.
 - `logue` - No prologue and epilogue will be generated.
 - `stchk` - No check for stack overflow and integer overflow will be generated.

---

### extern

The `extern` directive is used to define a function as an external function.

```wind
@extern func foo();
```

---

### pub

The `pub` directive is used to define a function as public.
While public directive is not required for including functions, it is used to share functions between objects when linking.

```wind
@pub func foo() {}
```

---

### type

The `type` directive is used to define a type.

```wind
@type my_type = unsigned byte;
```

---

### linkflag

The `linkflag` directive is used to define an ld flag.

```wind
@linkflag("-lm);
```

---

## Keywords

Wind has no concept of reserved-identifiers, so you can use any keyword as an identifier if you wish. However, the following keywords are used in the language and should be avoided as identifiers:

```rs
func
var
global
return
branch
else
loop
continue
break
asm
true
false
Null
```

---

## Data Types

Wind has some primitive data types:
```c
byte = signed 8 bits
short = signed 16 bits
int = signed 32 bits
long = signed 64 bits

unsigned byte = unsigned 8 bits
...
```

But the "#types.w" std file provides some more types:
```c
int8 = signed 8 bits
int16 = signed 16 bits
int32 = signed 32 bits
int64 = signed 64 bits

uint8 = unsigned 8 bits
uint16 = unsigned 16 bits
uint32 = unsigned 32 bits
uint64 = unsigned 64 bits

bool = 8 bits
char = 8 bits
```

Arrays are declared using the following syntax:

```wind
var arr: [int; 10];
```

### Pointers

Pointers are declared using the following syntax:

```wind
var ptr: ptr<int>;
```

Wind convention is to use heap allocation over stack allocated arrays.

with the `guard![]` directive, you can check for null pointers and prevent dereferencing.

```wind
var my_ptr: ptr<char> = guard![malloc(32)];
```

---

### Casting

Casting in Wind is done with the directive `cast<>()`
(Will be replaced with `as` in the future)

```wind
var x: ptr<uint64> = malloc(...);
cast<ptr<char>>(x)[0]='x';
```

---

## Variables

Variables in Wind are declared using the `var` keyword, followed by the variable name and type.

```wind
var x: int = 10;
```

You can declared them in bulk as well.

```wind
var [x,y,z]: int = 0;
```

---

## Global Variables

Global variables are declared using the `global` keyword.

```wind
global x: int = 10;
```

Non declarable in bulk.

---

## Functions

Functions in Wind are declared using the `func` keyword, followed by the function name, parameters, and return type.

```wind
func add(x: int, y: int): int {
   return x + y;
}
```

There's no wrapper for variadic functions, but you can still use `...` for external C functions.

```wind
@extern func printf(format: string, ...): int;
```

---

## Control Flow

Wind has the usual control flow features with unique syntax.

### Branch

The `branch` keyword is used to define a conditional statement.

```wind
branch [
   x == 0: puts("x is zero");
   else: {
      puts("x != 0);
      return 1;
   }
]
```

---

### Loop

The `loop` keyword is used to define a loop statement.

```wind
loop [x < 10] {
   puts("x is less than 10");
   x++;
}
```

There's no `for` loop in Wind, but you can use the `loop` keyword with a counter.

---

### Continue

The `continue` keyword is used to skip the current iteration of a loop.

```wind
loop [x < 10] {
   x++;
   continue;
}
```

### Break

The `break` keyword is used to exit a loop.

```wind
loop [x < 10] {
   x++;
   break;
}
```

---

## Inline Assembly

Wind supports inline assembly using the `asm` keyword.

```wind
asm {
   mov eax, 10;
   add eax, 20;
}
```

You can also reference local variables in inline assembly.

```wind
asm {
   mov eax, ?x;
   add eax, 0x10;
}
```

---

Happy coding with Wind! 🎉