# Float-Pointing Numbers

* 通常，`float` 为 `32` 位，`double` 为 `64` 位，`long double` 为 `80`、`96` 或 `128` 位。另外，这三种类型的指数范围**至少**是 `-37` 到 `37`，可以从头文件 `cfloat` 中找到系统的限制。

```cpp
#include <iostream>
#include <cfloat>
using namespace std;

int main() {
	cout << sizeof(float) << " " << sizeof(double) << " " << sizeof(long double) << endl;	// 4 8 8
	cout << FLT_MIN << " " << DBL_MIN << " " << LDBL_MIN << endl;	// 1.17549e-38 2.22507e-308 2.22507e-308
	cout << FLT_MAX << " " << DBL_MAX << " " << LDBL_MAX << endl;	// 3.40282e+38 1.79769e+308 1.79769e+308
	return 0;
}
```

* 在默认情况下，像 `8.24` 和 **`2.4E8`** 这样的浮点常量都属于 `double` 类型。如果希望常量为 `float` 类型，请使用 `f` 或 `F` 后缀。对于 `long double` 类型，可使用 `l` 或 `L` 后缀（由于 `l` 看起来像数字 `1`，因此 `L` 是更好的选择）。

## `double`

```cpp
scanf("%lf", &d);
printf("%f", d);
```

