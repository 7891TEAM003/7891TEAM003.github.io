---
layout: post
title:  "0x0002 - Structure of a program"
date:   2024-10-28 23:07:20 +0800
---
# Structure of a program
page: [https://cplusplus.com/doc/tutorial/program_structure/](https://cplusplus.com/doc/tutorial/program_structure/) <br/>
r2: [https://github.com/radareorg/radare2](https://github.com/radareorg/radare2)

```c++
// my first program in C++
#include <iostream>

int main()
{
  std::cout << "Hello World!";
}
```

**第一行：**`// my first program in C++` <br/>
"双斜杠" 这是注释内容，增加代码的可以读性。对程序没有任何影响。

**第二行：**`#include <iostream>` <br/>
由 `#` 开头表示这一个预处理器解释和读取的指令。<br/>
`include <iostream>` 表示包含了一个 `iostream` 库文件。<br/>
如果你想知道 g++ 在编译的时候使用哪些库，可以使用 `echo | g++ -E -v -` 命令。
```bash
➜  2-BasicsOfC++ echo | g++ -x c++ -E -v -
Using built-in specs.
COLLECT_GCC=g++
Target: x86_64-pc-linux-gnu
Configured with: /build/gcc/src/gcc/configure --enable-languages=ada,c,c++,d,fortran,go,lto,m2,objc,obj-c++,rust --enable-bootstrap --prefix=/usr --libdir=/usr/lib --libexecdir=/usr/lib --mandir=/usr/share/man --infodir=/usr/share/info --with-bugurl=https://gitlab.archlinux.org/archlinux/packaging/packages/gcc/-/issues --with-build-config=bootstrap-lto --with-linker-hash-style=gnu --with-system-zlib --enable-__cxa_atexit --enable-cet=auto --enable-checking=release --enable-clocale=gnu --enable-default-pie --enable-default-ssp --enable-gnu-indirect-function --enable-gnu-unique-object --enable-libstdcxx-backtrace --enable-link-serialization=1 --enable-linker-build-id --enable-lto --enable-multilib --enable-plugin --enable-shared --enable-threads=posix --disable-libssp --disable-libstdcxx-pch --disable-werror
Thread model: posix
Supported LTO compression algorithms: zlib zstd
gcc version 14.2.1 20240910 (GCC) 
COLLECT_GCC_OPTIONS='-E' '-v' '-shared-libgcc' '-mtune=generic' '-march=x86-64'
 /usr/lib/gcc/x86_64-pc-linux-gnu/14.2.1/cc1plus -E -quiet -v -D_GNU_SOURCE - -mtune=generic -march=x86-64 -dumpbase -
ignoring nonexistent directory "/usr/lib/gcc/x86_64-pc-linux-gnu/14.2.1/../../../../x86_64-pc-linux-gnu/include"
#include "..." search starts here:
#include <...> search starts here:
 /usr/lib/gcc/x86_64-pc-linux-gnu/14.2.1/../../../../include/c++/14.2.1
 /usr/lib/gcc/x86_64-pc-linux-gnu/14.2.1/../../../../include/c++/14.2.1/x86_64-pc-linux-gnu
 /usr/lib/gcc/x86_64-pc-linux-gnu/14.2.1/../../../../include/c++/14.2.1/backward
 /usr/lib/gcc/x86_64-pc-linux-gnu/14.2.1/include
 /usr/local/include
 /usr/lib/gcc/x86_64-pc-linux-gnu/14.2.1/include-fixed
 /usr/include
End of search list.
# 0 "<stdin>"
# 0 "<built-in>"
# 0 "<command-line>"
# 1 "/usr/include/stdc-predef.h" 1 3 4
# 0 "<command-line>" 2
# 1 "<stdin>"
COMPILER_PATH=/usr/lib/gcc/x86_64-pc-linux-gnu/14.2.1/:/usr/lib/gcc/x86_64-pc-linux-gnu/14.2.1/:/usr/lib/gcc/x86_64-pc-linux-gnu/:/usr/lib/gcc/x86_64-pc-linux-gnu/14.2.1/:/usr/lib/gcc/x86_64-pc-linux-gnu/
LIBRARY_PATH=/usr/lib/gcc/x86_64-pc-linux-gnu/14.2.1/:/usr/lib/gcc/x86_64-pc-linux-gnu/14.2.1/../../../../lib/:/lib/../lib/:/usr/lib/../lib/:/usr/lib/gcc/x86_64-pc-linux-gnu/14.2.1/../../../:/lib/:/usr/lib/
COLLECT_GCC_OPTIONS='-E' '-v' '-shared-libgcc' '-mtune=generic' '-march=x86-64
```

是这些目录。
```bash
#include "..." search starts here:
#include <...> search starts here:
 /usr/lib/gcc/x86_64-pc-linux-gnu/14.2.1/../../../../include/c++/14.2.1
 /usr/lib/gcc/x86_64-pc-linux-gnu/14.2.1/../../../../include/c++/14.2.1/x86_64-pc-linux-gnu
 /usr/lib/gcc/x86_64-pc-linux-gnu/14.2.1/../../../../include/c++/14.2.1/backward
 /usr/lib/gcc/x86_64-pc-linux-gnu/14.2.1/include
 /usr/local/include
 /usr/lib/gcc/x86_64-pc-linux-gnu/14.2.1/include-fixed
 /usr/include
End of search list.
```

**第三行：**空行<br/>
对编译器没有任何印象，只是增加可以阅读性<br/>
你甚至可以把代码写成这样，但是没有任何可以阅读性。<br/>
```c++
// my first program in C++
#include <iostream> 
int main(){std::cout << "Hello World!";}
```

**第四行：**`int main()`<br/>
这是个程序默认的开始位置，但是程序不会直接从 `main()` 开始运行，会先执行一些其他的东西。这个以后在讲。

**第五行和七行：**`{}`<br/>
`main()` 的代码应该在这两个括号里面。

**第六行：**`std::cout << "Hello World!";`
1. `std::cout`输出方法，std 代表 **st**andar**d** **c**haracter **out**put device。
2. `<<` 这是插入运算符。
3. `"Hello World!"` 被插入到 `std::cout`。
4. `;` 代表着一行代码到此结束。对程序没有任何影响，只是将代码分成不同的行，增加阅读性。

## Comments
C++ 中两种不同的注释<br/>
`// 单行注释` 
```
/*
 多行注释
*/
```

## Using namespace std
在下面这个代码，你能看到 cout 前失去了 `std::`。
这是应为在第三行有 `using namespace std;` 将 `std` 命名空间引入了当前作用域。也就是说在这个 cpp 文件中你不需要在使用 `std::` 来限定了，这可以简化代码。但是最好还是不要使用，因为可以和别的头文件冲突，复杂就是简单。
```
// my first program in C++
#include <iostream>
using namespace std;

int main()
{
	cout << "Hello World!";
}
```

## 走进 main 方法
`$ g main` 编译 main.cpp 文件，在编译好后，会生成一个 main EFL文件。
```bash
➜  1-StructureOfAProgram g main.cpp 
Compilation successful. Executable: main
```

`$ r2 main` 逆向这个 main EFL文件。
```bash
➜  1-StructureOfAProgram r2 main
WARN: Relocs has not been applied. Please use `-e bin.relocs.apply=true` or `-e bin.cache=true` next time
[0x00001040]> aaa
INFO: Analyze all flags starting with sym. and entry0 (aa)
INFO: Analyze imports (af@@@i)
INFO: Analyze entrypoint (af@ entry0)
INFO: Analyze symbols (af@@@s)
INFO: Recovering variables
INFO: Analyze all functions arguments/locals (afva@@@F)
INFO: Analyze function calls (aac)
INFO: Analyze len bytes of instructions for references (aar)
INFO: Finding and parsing C++ vtables (avrr)
INFO: Analyzing methods
INFO: Recovering local variables (afva)
INFO: Type matching analysis for all functions (aaft)
INFO: Propagate noreturn information (aanr)
INFO: Use -AA or aaaa to perform additional experimental analysis
[0x00001040]> 
```

分析 main EFL 文件。
```bash
[0x00001040]> aaa
INFO: Analyze all flags starting with sym. and entry0 (aa)
INFO: Analyze imports (af@@@i)
INFO: Analyze entrypoint (af@ entry0)
INFO: Analyze symbols (af@@@s)
INFO: Recovering variables
INFO: Analyze all functions arguments/locals (afva@@@F)
INFO: Analyze function calls (aac)
INFO: Analyze len bytes of instructions for references (aar)
INFO: Finding and parsing C++ vtables (avrr)
INFO: Analyzing methods
INFO: Recovering local variables (afva)
INFO: Type matching analysis for all functions (aaft)
INFO: Propagate noreturn information (aanr)
INFO: Use -AA or aaaa to perform additional experimental analysis
[0x00001040]>
```

你可以使用 `$ r2 -A main` 等于 `$ r2 main` 后在 `aaa`。
```bash
➜  1-StructureOfAProgram r2 -A main
WARN: Relocs has not been applied. Please use `-e bin.relocs.apply=true` or `-e bin.cache=true` next time
INFO: Analyze all flags starting with sym. and entry0 (aa)
INFO: Analyze imports (af@@@i)
INFO: Analyze entrypoint (af@ entry0)
INFO: Analyze symbols (af@@@s)
INFO: Recovering variables
INFO: Analyze all functions arguments/locals (afva@@@F)
INFO: Analyze function calls (aac)
INFO: Analyze len bytes of instructions for references (aar)
INFO: Finding and parsing C++ vtables (avrr)
INFO: Analyzing methods
INFO: Recovering local variables (afva)
INFO: Type matching analysis for all functions (aaft)
INFO: Propagate noreturn information (aanr)
INFO: Use -AA or aaaa to perform additional experimental analysis
[0x00001040]> 
```

 `s main` 表示切换到 main 的位置，你可以看到 0x00001040 变成了 0x00001139。<br/>
 `pdf` 应该是 `print the disassemble function`，打印反汇编方法。
```bash
[0x00001040]> s main
[0x00001139]> pdf
            ; DATA XREF from entry0 @ 0x1058(r)
┌ 36: int main (int argc, char **argv, char **envp);
│           0x00001139      55             push rbp
│           0x0000113a      4889e5         mov rbp, rsp
│           0x0000113d      488d05c10e..   lea rax, str.Hello_World_   ; 0x2005 ; "Hello World!"
│           0x00001144      4889c6         mov rsi, rax
│           0x00001147      488d05f22e..   lea rax, obj.std::cout      ; loc.__bss_start
│                                                                      ; 0x4040
│           0x0000114e      4889c7         mov rdi, rax
│           0x00001151      e8dafeffff     call method std::basic_ostream<char, std::char_traits<char> >& std::operator<< <std::char_traits<char> >(std::basic_ostream<char, std::char_traits<char> >&, char const*) ; method.std::basic_ostream_char__std::char_traits_char____std::operator____std.char_traits_char____std::basic_ostream_char__std::char_traits_char_____char_const_
│           0x00001156      b800000000     mov eax, 0
│           0x0000115b      5d             pop rbp
└           0x0000115c      c3             ret
[0x00001139]>
```

我们应该关注这些东西
![](/pictures/Pastedimage20241028224350.png)

到这里就不在深入了。
