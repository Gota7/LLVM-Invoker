# LLVM-Invoker
Invoke LLVM to run bitcode, for easy executable distribution.

## Offsets
Hex edit these locations either manually or with your compiler program to instead point to your .bc file.

| Executable | Offset |
|------------|--------|
| armhf-linux-gnu.elf | 0x000B2569 |
| x86_64-linux-gnu.elf | 0x0016A009 |

## Using The Invoker
First thing to do is install LLVM, which must be done for the end user!

### Arch Based
`sudo pacman -S llvm`

### Debian Based
`sudo apt-get install llvm`

## Editing The Executable
To use the invoker, first hex edit the `h`s at the address to instead be the name of the file followed by a null terminator. For the hello world script, change it to `HelloWorld.bc` followed by a null terminator. This should be done by the compiler for your language. I would also recommend renaming the executable to match your program name.

![alt text](Example.png "Example hex edit.")

Once this is done, run the executable and it should run your .bc file as long as it is in the same folder. You can also pass the invoker arguments too!

## Compiling The Invoker
The invoker can be compiled with the command `clang++ invoke.cpp -o OUTPUTNAME -static`. Make sure it is static so it can run on the target platform without problems!
