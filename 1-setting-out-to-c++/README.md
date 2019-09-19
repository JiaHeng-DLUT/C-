# 1 Setting Out to C++

## `#include <iostream>`

* A preprocessor directive. 
* It causes the contents of the iostream file to be substituted for this directive before final compilation. \(这将导致在最终的编译之前 ，使用 `iostream` 文件的内容替换该编译指令。\)
* **原始文件没有被修改，而是将源代码文件和iostream 组合成一个复合文件，编译的下一阶段将使用该文件。**
* 这是一种典型的预处理器操作：在源代码被编译之前，替换或添加文本。

## `#define INT_MAX 0x3fffffff`

* 在 `C++` 编译过程中，首先将源代码传递给预处理器。在这里，`#define` 和 `#include` 一样，也是一个预处理器编译指令。该编译指令告诉预处理器：在程序中查找 `INT_MAX`，并将所有的`INT_MAX` 都替换为 `0x3fffffff`。因此 `#define` 编译指令的工作方式与文本编辑器或字处理器中的全局搜索并替换命令相似。

## `using namespace std;`

* It makes definitions made in the std namespace available to a program. 
* 使用 `std` 名称空间中定义的名称，而不必使用 `std::` 前缀，该条指令使 `std` 名称空间中的所有名称都可用。

## `main()`

* `main()` 被启动代码调用，启动代码是由编译器添加到程序中的，是程序和操作系统之间的桥梁。事实上，该函数头描述的是 **`main()` 和操作系统之间的接口**。
* 在 `C++` 中，让括号空着与在括号中使用 `void` 等效。
* 在 `C` 中，让括号空着意味着对是否接受参数保持沉默。

## `sizeof`

* `sizeof` 运算符返回类型或变量的长度 ，单位为字节。对类型名（如 `int`）使用 `sizeof` 运算符时，应将名称放在括号中；但对变量名（如 `a`）使用该运算符，括号是可选的：

  ```cpp
    int a;
    cout << sizeof(int) << endl;
    cout << sizeof a << endl;
  ```

## Declaration Statements and Variables

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

## Functions

* C++程序应当为程序中使用的每个函数提供原型。
* 原型只描述函数接口。
* 库文件中包含了函数的编译代码，而头文件中则包含了原型。
* 只包含 `cmath` 头文件可以提供原型，但不一定会导致编译器搜索正确的库文件。

