# 1 Setting Out to C++

## 1 Hello world 

### `#include <iostream>`

* A preprocessor directive. 
* It causes the contents of the iostream file to be substituted for this directive before final compilation. \(这将导致在最终的编译之前 ，使用 `iostream` 文件的内容替换该编译指令。\)
* **原始文件没有被修改，而是将源代码文件和iostream 组合成一个复合文件，编译的下一阶段将使用该文件。**
* 这是一种典型的预处理器操作：在源代码被编译之前，替换或添加文本。

### `#define INT_MAX 0x3fffffff`

* 在 `C++` 编译过程中，首先将源代码传递给预处理器。在这里，`#define` 和 `#include` 一样，也是一个预处理器编译指令。该编译指令告诉预处理器：在程序中查找 `INT_MAX`，并将所有的`INT_MAX` 都替换为 `0x3fffffff`。因此 `#define` 编译指令的工作方式与文本编辑器或字处理器中的全局搜索并替换命令相似。

### `using namespace std;`

* It makes definitions made in the std namespace available to a program. 
* 使用 `std` 名称空间中定义的名称，而不必使用 `std::` 前缀，该条指令使 `std` 名称空间中的所有名称都可用。

### `main()`

* `main()` 被启动代码调用，启动代码是由编译器添加到程序中的，是程序和操作系统之间的桥梁。事实上，该函数头描述的是 **`main()` 和操作系统之间的接口**。
* 在 `C++` 中，让括号空着与在括号中使用 `void` 等效。
* 在 `C` 中，让括号空着意味着对是否接受参数保持沉默。

### `cout`

* 从概念上看，输出是一个流，即从程序流出的一系列字符。`cout` 对象表示这种流，其属性是在 `iostream` 文件中定义的。`cout` 的对象属性包括一个插入运算符（`<<`），它可以将其右侧的信息插入到流中。
* 诸如 `endl` 等对于 `cout` 来说有特殊含义的特殊符号被称为控制符（`manipulator`）。
* 显示用引号括起的字符串时，通常使用换行符 `\n`，在其他情况下则使用控制符 `endl`。一个差别是，`endl` 确保程序继续运行前刷新输出（将其立即显示在屏幕上）；而使用 `\n` 不能提供这样的保证，这意味着在有些系统中，有时可能在您输入信息后才会出现提示。
* 在默认情况下，cout以十进制格式显示整数，而不管这些整数在程序中是如何书写的。
* 控制符 `dec`、`hex` 和 `oct`，分别用于指示 `cout` 以十进制、十六进制和八进制格式显示整数。
* `setf()` 这种调用迫使输出使用定点表示法，以便更好地了解精度，它防止程序把较大的值切换为 `E` 表示法，并使程序显示到小数点后6位。参数 `ios_base::fixed` 和 `ios_base::floatfield` 是通过包含 `iostream` 来提供的常量。
* 通常cout会删除结尾的零，调用 `cout.setf()` 将覆盖这种行为。

### `sizeof`

* `sizeof` 运算符返回类型或变量的长度 ，单位为字节。对类型名（如 `int`）使用 `sizeof` 运算符时，应将名称放在括号中；但对变量名（如 `a`）使用该运算符，括号是可选的：

  ```cpp
    int a;
    cout << sizeof(int) << endl;
    cout << sizeof a << endl;
  ```

### `#include <climits>`

* 头文件 `climits` 中包含了关于整型限制的信息。

### `const` 比 `#define` 好

* 首先，它能够明确指定类型。
* 其次，可以使用 `C++` 的作用域规则将定义限制在特定的函数或文件中（作用域规则描述了名称在各种模块中的可知程度）。
* 第三，可以将 `const` 用于更复杂的类型，如数组和结构体。

## 2 Declaration Statements and Variables

* The declaration statement in the program is called a **defining declaration statement**, or definition, for short. This means that its presence causes the compiler to **allocate memory space** for the variable. In more complex situations, you can also have reference declarations. These tell the computer to use a variable that has already been defined elsewhere. In general, **a declaration need not be a definition**.

  > * 变量的定义和声明：
  >   * 声明（`int a`）是仅仅告诉编译器，有个某类型的变量会被使用，但是编译器并不会为它分配任何内存。
  >   * 定义（`int b = 1`）就是分配了内存。
  >   * 声明不一定不是定义，而定义一定是定义。
  >   * `extern int a;` 仅仅是声明，有一个 `int` 变量 `a`，它一定是在另外其他地方定义的，所以编译器此时一定不会做什么分配内存的事，因为它就是声明，仅仅表明引用了一个符号，而这个符号是 `int` 类型的 `a` 而已。
  > * 函数的定义和声明：
  >   * 声明：一般在头文件里，让编译器知道这个函数的存在。
  >   * 定义：一般在源文件里，具体就是函数的实现过程，写明函数体。
  >
  > From: [c++中定义和声明有什么区别？](https://zhidao.baidu.com/question/337113067.html)

## 3 Functions

* C++程序应当为程序中使用的每个函数提供原型。
* 原型只描述函数接口。
* 库文件中包含了函数的编译代码，而头文件中则包含了原型。
* 只包含 `cmath` 头文件可以提供原型，但不一定会导致编译器搜索正确的库文件。
* **`main` 不是关键字**，由于它不是语言的组成部分。然而，它是一个必不可少的函数的名称。
* 在不使用 `cout` 对象进行输出的函数中，可以将 `cout` 用作变量名，但不能在同一个函数中同时将 `cout` 用作对象名和变量名。

