#operator< (C++11)
* system_error[meta header]
* std[meta namespace]
* error_category[meta class]
* function[meta id-type]

```cpp
bool operator<(const error_category& rhs) const noexcept;
```

##概要
`error_category`オブジェクトのポインタの小なり比較を行う。

自身のポインタが`rhs`オブジェクトへのポインタより小さい場合`true`を返し、そうでなければ`false`を返す。


##戻り値
`less<const error_category*>()(this, &rhs)`


##例外
投げない


##例
```cpp
#include <iostream>
#include <system_error>

int main()
{
  const std::error_category& a = std::generic_category();
  const std::error_category& b = std::generic_category();
  const std::error_category& c = std::system_category();

  std::cout << std::boolalpha;

  std::cout << (a < b) << std::endl;
  std::cout << (a < c) << std::endl;
}
```

###出力例
```
false
false
```

##バージョン
###言語
- C++11

###処理系
- [Clang](/implementation.md#clang): ??
- [GCC](/implementation.md#gcc): 
- [GCC, C++0x mode](/implementation.md#gcc): 4.6.1
- [ICC](/implementation.md#icc): ??
- [Visual C++](/implementation.md#visual_cpp) 10.0


##参照
