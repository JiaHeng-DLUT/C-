# 2 Dealing with Data

## `sizeof`

- `sizeof` 运算符返回类型或变量的长度 ，单位为字节。对类型名（如 `int`）使用 `sizeof` 运算符时，应将名称放在括号中；但对变量名（如 `a`）使用该运算符，括号是可选的：
  
    ```cpp
    int a;
    cout << sizeof(int) << endl;
    cout << sizeof a << endl;
    ```

## `#include <climits>`

- 头文件 `climits` 中包含了关于整型限制的信息。

## `#define INT_MAX 0x3fffffff` 

- 在 `C++` 编译过程中，首先将源代码传递给预处理器。在这里，`#define` 和 `#include` 一样，也是一个预处理器编译指令。该编译指令告诉预处理器：在程序中查找 `INT_MAX`，并将所有的`INT_MAX` 都替换为 `0x3fffffff`。因此 `#define` 编译指令的工作方式与文本编辑器或字处理器中的全局搜索并替换命令相似。

## `cout` 

- 在默认情况下，cout以十进制格式显示整数，而不管这些整数在程序中是如何书写的。
- 控制符 `dec`、`hex` 和 `oct`，分别用于指示 `cout` 以十进制、十六进制和八进制格式显示整数。
- `setf()` 这种调用迫使输出使用定点表示法，以便更好地了解精度，它防止程序把较大的值切换为 `E` 表示法，并使程序显示到小数点后6位。参数 `ios_base::fixed` 和 `ios_base::floatfield` 是通过包含 `iostream` 来提供的常量。
- 通常cout会删除结尾的零，调用 `cout.setf()` 将覆盖这种行为。

## `const` 比 `#define` 好
- 首先，它能够明确指定类型。
- 其次，可以使用 `C++` 的作用域规则将定义限制在特定的函数或文件中（作用域规则描述了名称在各种模块中的可知程度）。
- 第三，可以将 `const` 用于更复杂的类型，如数组和结构体。

## Simple Variables

- Names for Variables 
  - Names beginning with `two underscore characters` or with `an underscore character followed by an uppercase letter` are reserved for use by the implementation—that is, the compiler and the resources it uses. Names beginning with a single underscore character are reserved for use as global identifiers by the implementation.
  - The next-to-last point is a bit different from the preceding points because using a name such as __time_stop or _Donut doesn’t produce a compiler error; instead, it leads to undefined behavior. In other words, there’s no telling what the result will be. The reason there is no compiler error is that the names are not illegal but rather are reserved for the implementation to use. The bit about global names refers to where the names are declared; Chapter 4 touches on that topic.
  - C++ places no limits on the length of a name, and all characters in a name are significant. However, some platforms might have their own length limits.
  - The final point differentiates C++ from ANSI C (C99), which guarantees only that the first 63 characters in a name are significant. (In ANSI C, two names that have the same first 63 characters are considered identical, even if the 64th characters differ.)

## Choosing an Integer Type

- 如果知道变量可能表示的整数值大于 `16` 位整数的最大可能值，则使用 `long`。即使系统上 `int` 为 `32` 位，也应这样做。这样，将程序移植到 `16` 位系统时，就不会突然无法正常工作。
- 如果节省内存很重要，则应使用 `short` 而不是使用 `int`，即使它们的长度是一样的。例如，假设要将程序从 `int` 为 `16` 位的系统移到 `int` 为 `32` 位的系统，则用于存储 `int` 数组的内存量将加倍，但 `short` 数组不受影响。

## How `C++` Decides What Type a Constant Is


- 除非有理由存储为其他类型（如使用了特殊的后缀来表示特定的类型，或者值太大，不能存储为 `int`），否则 `C++` 将整型常量存储为 `int` 类型。
- 整数后面的 `l` 或 `L` 后缀表示该整数为 `long` 常量，`u` 或 `U` 后缀表示 `unsigned` 常量，`ul`（可以采用任何一种顺序，大写小写均可）表示 `unsigned long` 常量（由于小写 `l` 看上去像 `1`，因此应使用大写 `L` 作后缀）。
- 对于不带后缀的十六进制或八进制整数，将使用下面几种类型中能够存储该数的最小类型来表示：`int`、`unsigned int`、`long`、`unsigned long`、`long long`或 `unsigned long long`。在将 `40000` 表示为 `long` 的计算机系统中，十六进制数 `0x9C40`（`40000`） 将被表示为 `unsigned int`。这是因为十六进制常用来表示内存地址，而内存地址是没有符号的，因此，`unsigned int` 比 `long` 更适合用来表示 `16` 位的地址。

## `char` 

- 可以基于字符的八进制和十六进制编码来使用转义序列。例如，`Ctrl + Z` 的 `ASCII` 码为 `26`，对应的八进制编码为 `032`，十六进制编码为 `0x1a`。可以用下面的转义序列来表示该字符：`\032` 或 `\x1a`。将这些编码用单引号括起，可以得到相应的字符常量，如 `'\032'`，也可以将它们放在字符串中，如 `"hi\x1athere"`。
- 退格 `\b` 字符使光标向左退一格，但不会清除屏显。
- char在默认情况下既不是没有符号，也不是有符号。是否有符号由C++实现决定，这样编译器开发人员可以最大限度地将这种类型与硬件属性匹配起来。

## `wchar_t`

- `wchar_t`（宽字符类型）可以表示扩展字符集。`wchar_t` 类型是一种整数类型，它有足够的空间，可以表示系统使用的最大扩展字符集。
- `cin` 和 `cout` 将输入和输出看作是 `char` 流，因此不适于用来处理 `wchar\_t` 类型。`iostream` 头文件的最新版本提供了作用相似的工具—`wcin` 和 `wcout`，可用于处理 `wchar_t` 流。另外，可以通过加上前缀 `L` 来指示宽字符常量和宽字符串。下面的代码将字母 `P` 的 `wchar\_t` 版本存储到变量 `c` 中，并显示单词 `tall` 的 `wchar_t` 版本：

    ```c++
    wchar_t = L'P';
    wcout << L"tall" << endl;
    ```

- `char16_t` 和 `char32_t`，两者均无符号，前者长16位，后者长32位。`C++11` 使用前缀 `u` 表示 `char16_t` 字符常量和字符串常量，如 `u'C'` 和 `u"begood"`；并使用前缀 `U` 表示 `char32_t` 常量，如 `U'R'` 和 `U"dirtyrat"`。类型 `char16_t` 与 `/u00F6` 形式的通用字符名匹配，而类型 `char32_t` 与 `/U0000222B` 形式的通用字符名匹配。

## Float-Pointing Numbers

- 通常，`float` 为 `32` 位，`double` 为 `64` 位，`long double` 为 `80`、`96` 或 `128` 位。另外，这三种类型的指数范围至少是 `-37` 到 `37`，可以从头文件 `cfloat` 中找到系统的限制。
- 在默认情况下，像 `8.24` 和 `2.4E8` 这样的浮点常量都属于 `double` 类型。如果希望常量为 `float` 类型，请使用 `f` 或 `F` 后缀。对于 `long double` 类型，可使用 `l` 或 `L` 后缀（由于 `l` 看起来像数字 `1`，因此 `L` 是更好的选择）。

## Type Conversion 

- In particular, list initialization doesn’t permit narrowing, which is when the type of the variable may not be able to represent the assigned value. For example, conversions of floating types to integer types are not allowed. 
- `wchar_t` 被提升成为下列类型中第一个宽度足够存储 `wchar_t` 取值范围的类型：`int`、`unsigned int`、`long` 或 `unsigned long`。
- `C++` 将对 `char` 和 `short` 类型（`signed` and `unsigned`）应用整型提升。另外，为保持与传统 `C` 语言中大量代码的兼容性，在将参数传递给取消原型对参数传递控制的函数时，`C++` 将 `float` 参数提升为 `double`。
- `C++` 还引入了 `4` 个强制类型转换运算符，对它们的使用要求更为严格。在这四个运算符中，`static_cast<>` 可用于将值从一种数值类型转换为另一种数值类型。

## Summary

- 整型从最小到最大依次是：`bool`、`char`、`signed char`、`unsigned char`、`short`、`unsigned short`、`int`、`unsigned int`、`long`、`unsigned long` 以及 `C++11` 新增的 `long long` 和 `unsigned long long`，`wchar_t` 类型在这个序列中的位置取决于实现。`C++11` 新增了类型 `char16_t` 和 `char32_t`，它们的宽度足以分别存储 `16` 和 `32` 位的字符编码。`C++` 确保了 `char` 足够大，能够存储系统基本字符集中的任何成员，而 `wchar_t` 则可以存储系统扩展字符集中的任意成员。

|      |      |      |      |
| :--: | :--: | :--: | :--: |
|      |      |      |      |
|      |      |      |      |
|      |      |      |      |
|      |      |      |      |

## Chapter Review

|                           Question                           |                            Answer                            |
| :----------------------------------------------------------: | :----------------------------------------------------------: |
|        Why does C++ have more than one integer type?         | Having more than one integer type lets you choose the type that is best suited to a particular need. For example, you could use short to conserve space or long to guarantee storage capacity or to find that a particular type speeds up a particular calculation. |
| What safeguards does C++ provide to keep you from exceeding the limits of an integer type? | C++ provides no automatic safeguards to keep you from exceeding integer limits; you can use the `climits` header file to determine what the limits are. |
| `char grade = 65;` <br />`char grade = 'A';` <br />Are they equivalent? | The two statements are not really equivalent, although they have the same effect on some systems. Most importantly, the first statement assigns the letter A to grade only on a system using the ASCII code, while the second statement also works for other codes. Second, 65 is a type int constant, whereas 'A' is a type char constant. |
| How could you use C++ to find out which character the code 88 represents? Come up with at least two ways. | `char c = 88; cout << c << endl; // char type prints as character` <br/>        `cout.put(char(88)); // put() prints char as character` <br/>        `cout << char(88) << endl; // new-style type cast value to char <br/>` <br />`cout << (char)88 << endl; // old-style type cast value to char` |
| Assigning a long value to a float can result in a rounding error. What about assigning long to double? long long to double? | The answer depends on how large the two types are. If long is 4 bytes, there is no loss. That’s because the largest long value would be about 2 billion, which is 10 digits. Because double provides at least 13 significant figures, no rounding would be needed. The long long type, on the other hand, can reach 19 digits, which exceeds the 13 significant figures guaranteed for double. |

