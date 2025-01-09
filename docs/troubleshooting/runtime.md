### Troubleshooting: `ld: cannot find wrt.o: No such file or directory`

## Issue:
The error `ld: cannot find wrt.o: No such file or directory` occurs because Wind comes with a runtime that needs to be compiled within the compiler using CMake. This runtime is necessary for the successful linking of object files during the build process.

## Solution:
To resolve this issue, you can either reinstall the compiler or manually compile the runtime yourself.

1. **Reinstall the Compiler**: Reinstalling the compiler will ensure that the runtime is correctly included and compiled.

2. **Compile the Runtime Manually**: If you're running Wind from source, compile the runtime by running the following command:

```bash
wind src/runtime/stack.w src/runtime/handler.w src/runtime/start.w -ej -o RUNTIME_PATH
```

Here, `RUNTIME_PATH` refers to the path where you want to output the compiled runtime. If you're running Wind from source, this will likely be `src/runtime/wrt.o`.

## Additional Information:
- Ensure that your CMake configuration includes the runtime during the build process.
- If you continue to encounter issues, double-check your environment paths and installation steps.

## Related Links:
- [Wind Documentation](../index.md)
- [Installation Guide](../learn/install.md)
