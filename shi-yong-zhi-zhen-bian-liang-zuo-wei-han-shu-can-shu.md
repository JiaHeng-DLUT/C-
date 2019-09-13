# 使用指针变量作为函数参数

* 指针类型也可以作为函数参数的类型，这时视为**把变量的地址传入函数。如果在函数中这个地址中的元素进行改变，原先的数据就会确实地被改变**。示例如下：

  ```cpp
    #include <bits/stdc++.h>
    using namespace std;

    // 地址传递
    void change(int* a) {
        *a = 2;
    }

    int main() {
        int a = 1;
        change(&a);
        cout << a << endl;    // 2
        return 0;
    }
  ```

## **经典例子：使用指针作为参数，交换两个数**

* 函数在接收参数的过程中是单向一次性的值传递，在调用 `swap(x, y)` 时只是传进去了 `x` 和 `y` 的副本，`x` 和 `y` 的值不会交换。

  ```cpp
    void swap(int a, int b) {
        int temp = a;
        b = a;
        a = temp;
    }

    int x = 1, y = 2;
    swap(x, y); // 1 2
  ```

* 在调用 `swap(&x, &y)` 时传进去了 `x` 和 `y` 的地址的副本，地址中存放的内容可变，`x` 和 `y` 的值会交换。

  ```cpp
    void swap(int* a, int* b) {
        int temp = *a;
        *a = *b;
        *b = temp;
    }

    int x = 1, y = 2;
    swap(&x, &y); // 2 1
  ```

* 在调用 `swap(&x, &y)` 时传进去了 `x` 和 `y` 的地址的副本，`x` 和 `y` 的值不会交换。

  ```cpp
    void swap(int* a, int* b) {
        int* temp = a;
        b = a;
        a = temp;
    }

    int x = 1, y = 2;
    swap(x, y); // 1 2
  ```

* 由于函数中加了 `&`，因此在调用 `swap(&x, &y)` 时直接传进去了 `x` 和 `y` 的地址，直接交换了 `x` 和 `y` 的地址。

  ```cpp
    void swap(int*& a, int*& b) {
        int* temp = a;
        b = a;
        a = temp;
    }

    int x = 1, y = 2;
    swap(x, y); // 2 1
  ```

