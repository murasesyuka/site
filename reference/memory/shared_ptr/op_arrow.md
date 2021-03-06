#operator-> (C++11)
* memory[meta header]
* std[meta namespace]
* shared_ptr[meta class]
* function[meta id-type]

```cpp
T* operator->() const noexcept;
```

##概要
ポインタを通してオブジェクトにアクセスする。


##要件

```cpp
get() != nullptr
```
* get()[link ./get.md]


##戻り値
[`get()`](./get.md)


##例
```cpp
#include <iostream>
#include <memory>
#include <string>

int main()
{
  std::shared_ptr<std::string> p(new std::string("hello"));

  std::cout << p->c_str() << std::endl;
}
```

###出力
```
hello
```

##バージョン
###言語
- C++11

###処理系
- [GCC](/implementation.md#gcc): 4.3.6
- [Clang libc++, C++11 mode](/implementation.md#clang): 3.0
- [ICC](/implementation.md#icc): ?
- [Visual C++](/implementation.md#visual_cpp): 9.0 (TR1), 10.0, 11.0, 12.0
