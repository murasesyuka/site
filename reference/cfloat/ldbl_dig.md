#LDBL_DIG
* cfloat[meta header]

* macro[meta id-type]
```cpp
#define LDBL_DIG implementation-defined
```
* implementation-defined[italic]

##概要
n 桁の10進数を `long double` に変換し、また元に戻した場合に値が変わらないような n のうち最大のもの。
`std::`[`numeric_limits`](/reference/limits/numeric_limits.md)`<long double>::`[`digits10`](/reference/limits/numeric_limits/digits10.md) と等しい。
