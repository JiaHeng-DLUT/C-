# Summary

* 整型从最小到最大依次是：`bool`、`char`、`signed char`、`unsigned char`、`short`、`unsigned short`、`int`、`unsigned int`、`long`、`unsigned long` 以及 `C++11` 新增的 `long long` 和 `unsigned long long`，`wchar_t` 类型在这个序列中的位置取决于实现。`C++11` 新增了类型 `char16_t` 和 `char32_t`，它们的宽度足以分别存储 `16` 和 `32` 位的字符编码。`C++` 确保了 `char` 足够大，能够存储系统基本字符集中的任何成员，而 `wchar_t` 则可以存储系统扩展字符集中的任意成员。

| Name | Bits | Range |  |
| :---: | :---: | :---: | :---: |
| short | 16 | $$-2 ^ {15} \sim +2 ^ {15} - 1$$  | $$3 * 10 ^ 5$$  |
| int | 32 | $$-2 ^ {31} \sim +2 ^ {31} - 1$$  | $$2 * 10 ^ 9$$  |
| long | 32 | $$-2 ^ {31} \sim +2 ^ {31} - 1$$  | $$2 * 10 ^ 9$$  |
| long long | 64 | $$-2 ^ {63} \sim +2 ^ {63} - 1$$  | $$9 ^ {19}$$  |

