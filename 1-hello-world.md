# 2 Setting Out to C++

## 1 C++ Initiation

### Preprocessor `#include` directive 

- `#include` 编译指令导致 `iostream` 文件的内容随源代码文件的内容一起被发送给编译器。实际上，`iostream` 文件的内容将取代程序中的代码行 `#include <iostream>`。**原始文件没有被修改，而是将源代码文件和iostream 组合成一个复合文件，编译的下一阶段将使用该文件。**
- `#include <iostream>` 导致预处理器将iostream文件的内容添加到程序中。这是一种典型的预处理器操作：在源代码被编译之前，替换或添加文本。
- 这将导致在最终的编译之前 ，使用 i o s t r e a m文件的内容替换该编译指令 。 


### `using namespace` directive

- `using namespace std` 表明可以使用 `std` 名称空间中定义的名称，而不必使用 `std::` 前缀，该条指令使 `std` 名称空间中的所有名称都可用。这是一种偷懒的做法，在大型项目中存在潜在的问题。更好的方法是，**只使所需的名称可用**，这可以通过使用 `using` 声明来实现：

  ```c++
  using std::cout;
  using std::endl;
  using std::cin;
  ```
  
  3 ．它使得程序可以使用 s t d名称空间中的定义 。

### `main()` 

- `main()` 被启动代码调用，启动代码是由编译器添加到程序中的，是程序和操作系统之间的桥梁。事实上，该函数头描述的是 **`main()` 和操作系统之间的接口**。
- 在 `C++` 中，让括号空着与在括号中使用 `void` 等效。
- 在 `C` 中，让括号空着意味着对是否接受参数保持沉默。

### `cout` 

- 从概念上看，输出是一个流，即从程序流出的一系列字符。`cout` 对象表示这种流，其属性是在 `iostream` 文件中定义的。`cout` 的对象属性包括一个插入运算符（`<<`），它可以将其右侧的信息插入到流中。
- 诸如 `endl` 等对于 `cout` 来说有特殊含义的特殊符号被称为控制符（`manipulator`）。
- 显示用引号括起的字符串时，通常使用换行符 `\n`，在其他情况下则使用控制符 `endl`。一个差别是，`endl` 确保程序继续运行前刷新输出（将其立即显示在屏幕上）；而使用 `\n` 不能提供这样的保证，这意味着在有些系统中，有时可能在您输入信息后才会出现提示。

### C++ Source Code Style

## 2 C++ Statement 

- 一行代码中不可分割的元素叫做标记（token），空格、制表符和回车space, tab, or carriage return,统称为空白（white space）。The indivisible elements in a line of code are called tokens (see Figure 2.3). Generally, you
  must separate one token from the next with a space, tab, or carriage return, which collectively
  are termed white space.

### Declaration Statements and Variables

- The declaration statement in the program is called a defining declaration statement, or definition, for short. This means that its presence causes the compiler to allocate memory space for the variable. In more complex situations, you can also have reference declarations. These tell the computer to use a variable that has already been defined elsewhere. In general, **a declaration need not be a definition**, but in this example it is.
> - 变量的定义和声明：
  - 声明（`int a`）是仅仅告诉编译器，有个某类型的变量会被使用，但是编译器并不会为它分配任何内存。
  - 定义（`int b = 1`）就是分配了内存。
  - 声明不一定不是定义，而定义一定是定义。
  - `extern int a;` 仅仅是声明，有一个 `int` 变量 `a`，它一定是在另外其他地方定义的，所以编译器此时一定不会做什么分配内存的事，因为它就是声明，仅仅表明下面的代码引用了一个符号，而这个符号是 `int` 类型的 `a` 而已。
> - 函数的定义和声明：
  - 声明：一般在头文件里，让编译器知道这个函数的存在。
  - 定义：一般在源文件里，具体就是函数的实现过程，写明函数体。
> 
> From: [c++中定义和声明有什么区别？](https://zhidao.baidu.com/question/337113067.html)

## 3 Functions

- C++程序应当为程序中使用的每个函数提供原型。
- 原型只描述函数接口。
- 库文件中包含了函数的编译代码，而头文件中则包含了原型。
- 只包含 `cmath` 头文件可以提供原型，但不一定会导致编译器搜索正确的库文件。

- `C++` 不允许将函数定义嵌套在另一个函数定义中。每个函数定义都是独立的，所有函数的创建都是平等的。
- **`main` 不是关键字**，由于它不是语言的组成部分。然而，它是一个必不可少的函数的名称。
- 在不使用 `cout` 对象进行输出的函数中，可以将 `cout` 用作变量名，但不能在同一个函数中同时将 `cout` 用作对象名和变量名。

- 



声明语句：定义函数中使用的变量的名称和类型。赋值语句：使用赋值运算符（=）

Highlight (yellow) - 2.5 总结 > Location 1444

给变量赋值。消息语句：将消息发送给对象，激发某种行动。函数调用：执行函数。被调用的函数执行完毕后，程序返回到函数调用语句后面的语句。函数原型：声明函数的返回类型、函数接受的参数数量和类型。返回语句：将一个值从被调用的函数那里返回到调用函数中。

It causes the contents of the iostream file to be substituted for this directive before
final compilation.

3. It makes definitions made in the std namespace available to a program.