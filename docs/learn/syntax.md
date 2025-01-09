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

## Keywords

Wind has no concept of reserved-identifiers, so you can use any keyword as an identifier if you wish. However, the following keywords are used in the language:

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

But the "types.w" std file provides some more types:
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