# Wind Advanced Examples

Welcome to the Wind advanced examples! Here you'll find a collection of advanced code snippets that demonstrate the power and flexibility of the Wind programming language. These examples cover mainly runtime checks and memory management, showcasing how Wind can help you write safe and efficient code.

---

## Table of Contents

- [Memory Management](#memory-management)
- [Pointers and References](#pointers-and-references)

---

## Memory Management

Here's an example of how you can run read/write data from the user without having to worry about memory leaks, buffer overflows, integer over/underflows or any other memory-related issues.

```wind
@include[
    "#libc.w"
]

func main(): int {
    var buff: [char;32];
    __builtin_memset(buff, 0, 32);
    
    var user_i: int32;
    printf("name: ");
    scanf("%s", buff);
    printf("index: ");
    scanf("%d", &user_i);
    var user_c: char = buff[user_i];
    var square: int32 = user_i * user_i;
    printf("buff[%d] = %c ; Squared i = %d\n", user_i, user_c, square);
    return 0;
}
```

### Protection breakdown

 - `scanf("%s", buff)`:

    _No input limit? No problem! There's a canary check that will prevent return address overwrites._

- `buff[user_i]`:

    _Accessing an array out of bounds? Impossible! There are runtime checks that will prevent out-of-bounds access._

- `user_i * user_i`:
    
    _Integer overflow? Not a chance! Every unsafe arithmetic operation is checked for overflow._

## Pointers and References

Here's an example of how you can use pointers and references in Wind to create safe and efficient code.

```wind
@include[
    "#libc.w"
]

func get_ptr(): ptr<int> {
    var buff: ptr<int> = guard![malloc(32*900000000)];
    return buff;
}

func main(): int {
    var buff: ptr<int> = get_ptr();
    printf("Buff: %p\n", buff);
    return 0;
}
```

### Protection breakdown

- `malloc(32*900000000)`:

    _Null pointers? Not here! The `guard![]` directive will check for null pointers and prevent dereferencing._