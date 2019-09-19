# 2 Dealing with Data

## Names for Variables 

* Names beginning with `two underscore characters` or with `an underscore character followed by an uppercase letter` are reserved for use by the implementation—that is, the compiler and the resources it uses. Names beginning with a single underscore character are reserved for use as global identifiers by the implementation.
* The next-to-last point is a bit different from the preceding points because using a name such as \_\_time\_stop or \_Donut doesn’t produce a compiler error; instead, it leads to undefined behavior. In other words, there’s no telling what the result will be. The reason there is no compiler error is that the names are not illegal but rather are reserved for the implementation to use. The bit about global names refers to where the names are declared; Chapter 4 touches on that topic.
* C++ places no limits on the length of a name, and all characters in a name are significant. However, some platforms might have their own length limits.
* The final point differentiates C++ from ANSI C \(C99\), which guarantees only that the first 63 characters in a name are significant. \(In ANSI C, two names that have the same first 63 characters are considered identical, even if the 64th characters differ.\)

## Choosing an Integer Type

* 如果知道变量可能表示的整数值大于 `16` 位整数的最大可能值，则使用 `long`。即使系统上 `int` 为 `32` 位，也应这样做。这样，将程序移植到 `16` 位系统时，就不会突然无法正常工作。
* 如果节省内存很重要，则应使用 `short` 而不是使用 `int`，即使它们的长度是一样的。例如，假设要将程序从 `int` 为 `16` 位的系统移到 `int` 为 `32` 位的系统，则用于存储 `int` 数组的内存量将加倍，但 `short` 数组不受影响。

## How `C++` Decides What Type a Constant Is

* 除非有理由存储为其他类型（如使用了特殊的后缀来表示特定的类型，或者值太大，不能存储为 `int`），否则 `C++` 将整型常量存储为 `int` 类型。
* 整数后面的 `l` 或 `L` 后缀表示该整数为 `long` 常量，`u` 或 `U` 后缀表示 `unsigned` 常量，`ul`（可以采用任何一种顺序，大写小写均可）表示 `unsigned long` 常量（由于小写 `l` 看上去像 `1`，因此应使用大写 `L` 作后缀）。
* 对于不带后缀的十六进制或八进制整数，将使用下面几种类型中能够存储该数的最小类型来表示：`int`、`unsigned int`、`long`、`unsigned long`、`long long`或 `unsigned long long`。在将 `40000` 表示为 `long` 的计算机系统中，十六进制数 `0x9C40`（`40000`） 将被表示为 `unsigned int`。这是因为十六进制常用来表示内存地址，而内存地址是没有符号的，因此，`unsigned int` 比 `long` 更适合用来表示 `16` 位的地址。

## Type Conversion

* In particular, list initialization doesn’t permit narrowing, which is when the type of the variable may not be able to represent the assigned value. For example, conversions of floating types to integer types are not allowed. 
* `wchar_t` 被提升成为下列类型中第一个宽度足够存储 `wchar_t` 取值范围的类型：`int`、`unsigned int`、`long` 或 `unsigned long`。
* `C++` 将对 `char` 和 `short` 类型（`signed` and `unsigned`）应用整型提升。另外，为保持与传统 `C` 语言中大量代码的兼容性，在将参数传递给取消原型对参数传递控制的函数时，`C++` 将 `float` 参数提升为 `double`。
* `C++` 还引入了 `4` 个强制类型转换运算符，对它们的使用要求更为严格。在这四个运算符中，`static_cast<>` 可用于将值从一种数值类型转换为另一种数值类型。



