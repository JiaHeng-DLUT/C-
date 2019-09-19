# 3 Dealing with Data

### `sizeof`

* `sizeof` 运算符返回类型或变量的长度 ，单位为字节。对类型名（如 `int`）使用 `sizeof` 运算符时，应将名称放在括号中；但对变量名（如 `n_short`）使用该运算符，括号是可选的：
* ```cpp
  int a;
  cout << sizeof(int) << endl;
  cout << sizeof a << endl;
  ```
* 头文件 `climits` 中包含了关于整型限制的信息。
* 
Highlight\(blue\) - Location 1603

表 3 . 1 c l i m i t s中的符号常量

Highlight\(blue\) - Location 1641

在 C + +编译过程中 ，首先将源代码传递给预处理器 。在这里 ， \# d e f i n e和 \# i n c l u d e一样 ，也是一个预处理器编译指令 。该编译指令告诉预处理器 ：在程序中查找 I N T \_ M A X ，并将所有的 I N T \_ M A X都替换为 3 2 7 6 7 。因此 \# d e f i n e编译指令的工作方式与文本编辑器或字处理器中的全局搜索并替换命令相似 。修改后的程序将在完成这些替换后被编译 。预处理器查找独立的标记 （单独的单词 ） ，跳过嵌入的单词 。

Highlight\(blue\) - Location 1693

Highlight\(blue\) - Location 1698

如果知道变量可能表示的整数值大于 1 6位整数的最大可能值 ，则使用 l o n g 。即使系统上 i n t为 3 2位 ，也应这样做 。这样 ，将程序移植到 1 6位系统时 ，就不会突然无法正常工作 （参见图 3 . 2 ） 。如果要存储的值超过 2 0亿 ，可使用 l o n g l o n g 。

Highlight\(blue\) - Location 1704

如果节省内存很重要 ，则应使用 s h o r t而不是使用 i n t ，即使它们的长度是一样的 。例如 ，假设要将程序从 i n t为 1 6位的系统移到 i n t为 3 2位的系统 ，

Highlight\(blue\) - Location 1705

则用于存储 i n t数组的内存量将加倍 ，但 s h o r t数组不受影响 。请记住 ，节省一点就是赢得一点 。如果只需要一个字节 ，可使用 c h a r

Highlight\(blue\) - Location 1715

在默认情况下 ， c o u t以十进制格式显示整数 ，而不管这些整数在程序中是如何书写的

Highlight\(blue\) - Location 1722

控制符 d e c 、 h e x和 o c t ，分别用于指示 c o u t以十进制 、十六进制和八进制格式显示整数

Highlight\(blue\) - Location 1732

程序将把 1 4 9 2存储为 i n t 、 l o n g还是其他整型呢 ？答案是 ，除非有理由存储为其他类型 （如使用了特殊的后缀来表示特定的类型 ，或者值太大 ，不能存储为 i n t ） ，否则 C + +将整型常量存储为 i n t类型 。

Highlight\(blue\) - Location 1736

整数后面的 l或 L后缀表示该整数为 l o n g常量 ， u或 U后

Highlight\(blue\) - Location 1736

缀表示 u n s i g n e d i n t常量 ， u l （可以采用任何一种顺序 ，大写小写均可 ）表示 u n s i g n e d l o n g常量 （由于小写 l看上去像 1 ，因此应使用大写 L作后缀 ） 。

Highlight\(blue\) - Location 1739

C + + 1 1提供了用于表示类型 l o n g l o n g的后缀 l l和 L L ，还提供了用于表示类型 u n s i g n e d l o n g l o n g的后缀 u l l 、 U l l 、 u L L和 U L L 。

Highlight\(blue\) - Location 1743

对于不带后缀的十六进制或八进制整数 ，将使用下面几种类型中能够存储该数的最小类型来表示 ： i n t 、 u n s i g n e d i n t l o n g 、 u n s i g n e d l o n g 、 l o n g l o n g或 u n s i g n e d l o n g l o n g 。在将 4 0 0 0 0表示为 l o n g的计算机系统中 ，十六进制数 0 x 9 C 4 0 （ 4 0 0 0 0 ）将被表示为 u n s i g n e d i n t 。这是因为十六进制常用来表示内存地址 ，而内存地址是没有符号的 ，因此 ， u n s i g n e d i n t比 l o n g更适合用来表示 1 6位的地址 。

Highlight\(pink\) - Location 1790

在 C + +的 R e l e a s e 2 . 0之前 ， c o u t将字符变量显示为字符 ，而将字符常量 （如 ‘ M ’和 ‘ N ’ ）显示为数字 。问题是 ， C + +的早期版本与 C一样 ，也将把字符常量存储为 i n t类型 。也就是说 ， ‘ M ’的编码 7 7将被存储在一个 1 6位或 3 2位的单元中 。而 c h a r变量一般占 8位 。下面的语句从常量 ‘ M ’中复制 8位 （左边的 8位 ）到变量 c h中 ：遗憾的是 ，这意味着对 c o u t来说 ， ‘ M ’和 c h看上去有天壤之别 ，虽然它们存储的值相同 。因此 ，下面的语句将打印 $字符的 A S C I I码 ，而不是字符 $ ：但下面的语句将打印字符 $ ：

Highlight\(blue\) - Location 1810

\ a表示振铃字符 ，它可以使终端扬声器振铃 。转义序列 \ n表示换行符 ， \ ”将双引号作为常规字符 ，而不是字符串分隔符 。

Highlight\(blue\) - Location 1815

表 3 . 2 C + +转义序列的编码

Highlight\(blue\) - Location 1866

可以将换行符嵌入到较长的字符串中 ，这通常比使用 e n d l方便 。

Highlight\(blue\) - Location 1868

显示数字时 ，使用 e n d l比输入 “ \ n ”或 ‘ \ n ’更容易些 ，但显示字符串时 ，在字符串末尾添加一个换行符所需的输入量要少些

Highlight\(orange\) - Location 1870

可以基于字符的八进制和十六进制编码来使用转义序列 。例如 ， C t r + Z的 A S C I I码为 2 6 ，对应的八进制编码为 0 3 2 ，十六进制编码为 0 x 1 a 。可以用下面的转义序列来表示该字符 ： \ 0 3 2或 \ x 1 a 。将这些编码用单引号括起 ，可以得到相应的字符常量 ，如 ' \ 0 3 2 ' ，也可以将它们放在字符串中 ，如 " h i \ x 1 a t h e r e " 。

Highlight\(orange\) - Location 1877

使用退格字符使光标向左退一格

Note - Location 1878

但没有清除屏显

Highlight\(blue\) - Location 1920

c h a r在默认情况下既不是没有符号 ，也不是有符号 。是否有符号由 C + +实现决定 ，这样编译器开发人员可以最大限度地将这种类型与硬件属性匹配起来 。

Highlight\(blue\) - Location 1930

w c h a r \_ t （宽字符类型 ）可以表示扩展字符集 。 w c h a r \_ t类型是一种整数类型 ，它有足够的空间 ，可以表示系统使用的最大扩展字符集 。

Highlight\(blue\) - Location 1933

c i n和 c o u t将输入和输出看作是 c h a r流 ，因此不适于用来处理 w c h a r \_ t类型 。 i o s t r e a m头文件的最新版本提供了作用相似的工具—w c i n和 w c o u t ，可用于处理 w c h a r \_ t流 。另外 ，可以通过加上前缀 L来指示宽字符常量和宽字符串 。下面的代码将字母 P的 w c h a r \_ t版本存储到变量 b o b中 ，并显示单词 t a l l的 w c h a r \_ t版本 ：

Highlight\(blue\) - Location 1942

c h a r 1 6 \_ t和 c h a r 3 2 \_ t ，其中前者是无符号的 ，长 1 6位 ，而后者也是无符号的 ，但长 3 2位 。 C + + 1 1使用前缀 u表示 c h a r 1 6 \_ t字符常量和字符串常量 ，如 u ‘ C ’和 u “ b e g o o d ” ；并使用前缀 U表示 c h a r 3 2 \_ t常量 ，如 U ‘ R ’和 U “ d i r t y r a t ” 。类型 c h a r 1 6 \_ t与 / u 0 0 F 6形式的通用字符名匹配 ，而类型 c h a r 3 2 \_ t与 / U 0 0 0 0 2 2 2 B形式的通用字符名匹配 。

Highlight\(blue\) - Location 1975

c o n s t比 \# d e f i e n好 。首先 ，它能够明确指定类型 。其次 ，可以使用 C + +的作用域规则将定义限制在特定的函数或文件中 （作用域规则描述了名称在各种模块中的可知程度 ，将在第 9章讨论 ） 。第三 ，可以将 c o n s t用于更复杂的类型 ，如第 4章将介绍的数组和结构 。

Highlight\(blue\) - Location 2019

通常 ， f l o a t为 3 2位 ， d o u b l e为 6 4位 ， l o n g d o u b l e为 8 0 、 9 6或 1 2 8位 。另外 ，这 3种类型的指数范围至少是 − 3 7到 3 7 。可以从头文件 c f l o a t或 f l o a t . h中找到系统的限制

Highlight\(blue\) - Location 2026

s e t f \( \) 。这种调用迫使输出使用定点表示法 ，以便更好地了解精度 ，它防止程序把较大的值切换为 E表示法 ，并使程序显示到小数点后 6位 。参数 i o s \_ b a s e : : f i x e d和 i o s \_ b a s e : : f l o a t f i e l d是通过包含 i o s t r e a m来提供的常量 。

Highlight\(blue\) - Location 2031

通常 c o u t会删除结尾的零

Highlight\(blue\) - Location 2032

调用 c o u t . s e t f \( \)将覆盖这种行为

Highlight\(blue\) - Location 2049

在默认情况下 ，像 8 . 2 4和 2 . 4 E 8这样的浮点常量都属于 d o u b l e类型 。如果希望常量为 f l o a t类型 ，请使用 f或 F后缀 。对于 l o n g d o u b l e类型 ，可使用 l或 L后缀 （由于 l看起来像数字 1 ，因此 L是更好的选择 ） 。

Highlight\(blue\) - Location 2068

f l o a t 、 d o u b l e和 l o n g d o u b l e统称为浮点型 。整数和浮点型统称算术 （ a r i t h m e t i c ）类型 。

Highlight\(blue\) - Location 2083

Highlight\(blue\) - Location 2131

相同的符号进行多种操作叫做运算符重载 （ o p e r a t o r o v e r l o a d i n g ） 。

Highlight\(pink\) - Location 2187

具体地说 ，列表初始化不允许缩窄 （ n a r r o w i n g ） ，即变量的类型可能无法表示赋给它的值 。

Highlight\(blue\) - Location 2197

在计算表达式时 ， C + +将 b o o l 、 c h a r 、 u n s i g n e d c h a r 、 s i g n e d c h a r和 s h o r t值转换为 i n t 。具体地说 ， t r u e被转换为 1 ， f a l s e被转换为 0 。这些转换被称为整型提升 （ i n t e g r a l p r o m o t i o n ） 。

Highlight\(blue\) - Location 2205

w c h a r \_ t被提升成为下列类型中第一个宽度足够存储 w c h a r \_ t取值范围的类型 ： i n t 、 u n s i g n e d i n t 、 l o n g或 u n s i g n e d l o n g 。

Highlight\(blue\) - Location 2222

有符号整型按级别从高到低依次为 l o n g l o n g 、 l o n g 、 i n t 、 s h o r t和 s i g n e d c h a r 。无符号整型的排列顺序与有符号整型相同 。类型 c h a r 、 s i g n e d c h a r和 u n s i g n e d c h a r的级别相同 。类型 b o o l的级别最低 。 w c h a r \_ t 、 c h a r 1 6 \_ t和 c h a r 3 2 \_ t的级别与其底层类型相同 。

Highlight\(blue\) - Location 2226

C + +将对 c h a r和 s h o r t类型 （ s i g n e d和 u n s i g n e d ）应用整型提升 。另外 ，为保持与传统 C语言中大量代码的兼容性 ，在将参数传递给取消原型对参数传递控制的函数时 ， C + +将 f l o a t参数提升为 d o u b l e 。

Highlight\(blue\) - Location 2234

第一种格式来自 C语言 ，第二种格式是纯粹的 C + + 。新格式的想法是 ，要让强制类型转换就像是函数调用 。这样对内置类型的强制类型转换就像是为用户定义的类设计的类型转换 。

Highlight\(blue\) - Location 2237

C + +还引入了 4个强制类型转换运算符 ，对它们的使用要求更为严格 ，这将在第 1 5章介绍 。在这四个运算符中 ， s t a t i c \_ c a s t &lt; &gt;可用于将值从一种数值类型转换为另一种数值类型 。例如 ，可以像下面这样将 t h o r n转换为 l o n g类型 ：推而广之 ，可以这样做 ： S t r o u s t r u p认为 ， C语言式的强制类型转换由于有过多的可能性而极其危险 ，这将在第 1 5章更深入地讨论 。运算符 s t a t i c \_ c a s t &lt; &gt;比传统强制类型转换更严格 。

Highlight\(blue\) - Location 2275

整型从最小到最大依次是 ： b o o l 、 c h a r 、 s i g n e d c h a r 、 u n s i g n e d c h a r 、 s h o r t 、 u n s i g n e d s h o r t 、 i n t 、 u n s i g n e d i n t 、 l o n g 、 u n s i g n e d l o n g以及 C + + 1 1新增的 l o n g l o n g和 u n s i g n e d l o n g l o n g 。还有一种 w c h a r \_ t类型 ，它在这个序列中的位置取决于实现 。 C + + 1 1新增了类型 c h a r 1 6 \_ t和 c h a r 3 2 \_ t ，它们的宽度足以分别存储 1 6和 3 2位的字符编码 。 C + +确保了 c h a r足够大 ，能够存储系统基本字符集中的任何成员 ，而 w c h a r \_ t则可以存储系统扩展字符集中的任意成员 ， s h o r t至少为 1 6位 ，而 i n t至少与 s h o r t一样长 ， l o n g至少为 3 2位 ，且至少和 i n t一样长 。确切的长度取决于实现 。

Highlight\(blue\) - Location 2283

长 。通常 ， f l o a t使用 3 2位内存 ， d o u b l e使用 6 4位 ， l o n g d o u b l e使用 8 0到 1 2 8位 。



### Chapter Review

<table>
  <thead>
    <tr>
      <th style="text-align:center">Question</th>
      <th style="text-align:center">Answer</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:center">Why does C++ have more than one integer type?</td>
      <td style="text-align:center">Having more than one integer type lets you choose the type that is best
        suited to a particular need. For example, you could use short to conserve
        space or long to guarantee storage capacity or to find that a particular
        type speeds up a particular calculation.</td>
    </tr>
    <tr>
      <td style="text-align:center">
        <p>What safeguards does C++ provide to keep you from exceeding the limits
          of an</p>
        <p>integer type?</p>
      </td>
      <td style="text-align:center">C++ provides no automatic safeguards to keep you from exceeding integer
        limits; you can use the <code>climits</code> header file to determine what
        the limits are.</td>
    </tr>
    <tr>
      <td style="text-align:center"><code>char grade = 65;</code>  <code>char grade = &apos;A&apos;;</code> Are
        they equivalent?</td>
      <td style="text-align:center">The two statements are not really equivalent, although they have the same
        effect on some systems. Most importantly, the first statement assigns the
        letter A to grade only on a system using the ASCII code, while the second
        statement also works for other codes. Second, 65 is a type int constant,
        whereas &apos;A&apos; is a type char constant.</td>
    </tr>
    <tr>
      <td style="text-align:center">How could you use C++ to find out which character the code 88 represents?
        Come up with at least two ways.</td>
      <td style="text-align:center"><code>char c = 88; cout &lt;&lt; c &lt;&lt; endl; // char type prints as character</code>
        <br
        /><code>cout.put(char(88)); // put() prints char as character </code>
        <br
        /><code>cout &lt;&lt; char(88) &lt;&lt; endl; // new-style type cast value to char</code> 
        <br
        /><code>cout &lt;&lt; (char)88 &lt;&lt; endl; // old-style type cast value to char</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:center">
        <p>Assigning a long value to a float can result in a rounding error.What
          about</p>
        <p>assigning long to double? long long to double?</p>
      </td>
      <td style="text-align:center">The answer depends on how large the two types are. If long is 4 bytes,
        there is no loss.That&#x2019;s because the largest long value would be
        about 2 billion, which is 10 digits. Because double provides at least 13
        significant figures, no rounding would be needed.The long long type, on
        the other hand, can reach 19 digits, which exceeds the 13 significant figures
        guaranteed for double.</td>
    </tr>
  </tbody>
</table>

