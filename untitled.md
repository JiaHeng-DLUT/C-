---
description: 读取字符串的效率比较
---

# scanf, fgets, cin and getline

## 对比数据

* `ios::sync_with_stdio(true);` 

| 读取函数 | `fgets` | `scanf` | `cin` | `getline` |
| :---: | :---: | :---: | :---: | :---: |
| 所用时间 | 295 ms | 424 ms | 2522 ms | 4613 ms |

* `ios::sync_with_stdio(false);` 

| 读取函数 | `fgets` | `scanf` | `cin` | `getline` |
| :---: | :---: | :---: | :---: | :---: |
| 所用时间 | 291 ms | 420 ms | 2482 ms | 4413 ms |

## 结论

* `fgets` 函数读取字符串的速度最快，读取时间约为 `scanf` 函数的 70%，约为 `cin` 的 2/17，约为 `getline` 的 1/15，因此在读取字符串时，如果字符串很长，应尽可能使用 `fgets` 函数，具体使用方法见 [fgets\(\)](https://snippets.cacher.io/snippet/3b9dbdf35b7349c17fef)。
* `scanf` 函数的读取时间约为 `getline` 的 1/6，约为 `cin` 的 1/10。
* `cin` 比 `getline` 快大约一倍。

## 为什么会出现这样的情况呢❓

> 1. 以 `fgets` 函数和 `scanf` 函数为例，由于 `fgets` 只负责读取字符串，而 `scanf` 函数还可以读取其他如 `int`、`double` 类型的数据，所以 `scanf` 函数就多了确定读取的数据是何种类型的步骤，因而花费了更多的时间。
> 2. `getline` 和 `cin` 函数只能向 `string` 类型中读入数据，由于 `string` 类型是在堆上分配的，在读取数据的时候需要不断从堆上申请动态分配内存，不如 char 数组直接提前分配好了所有内存来得更为简便。此外在向 `string` 类型读入数据的时候，还需要调用 `string` 类型的构造函数，初始化包括 `begin()`、`end()`、`size()` 等类内数据成员和成员函数，这也花费了很多时间。所以 `string` 类型比 `char` 数组提供了许多使用更为简便的函数和成员，但也要为此承担时间上的代价。

## References

1. [C语言中scanf、gets、fgets，C++中cin、getline读取字符串的效率比较](https://blog.csdn.net/richenyunqi/article/details/89203826)
2. [读取字符串函数 \[string\] \[char \*\]](https://github.com/hanchenchen/CCplusplus/blob/master/读取字符串函数%20[string].md)

