#addressof (C++11)
* memory[meta header]
* std[meta namespace]
* function template[meta id-type]

```cpp
namespace std {
  template <class T>
  T* addressof(T& r) noexcept;
}
```

##概要
変数のアドレスを必ず取得する。

`operator&()` をオーバーロードしたクラスであっても、正しくそのオブジェクトのアドレスが欲しいという要求がある。
`addressof()`関数は、`operator&()` がオーバーロードされていても、変数のアドレスを取得できる。


##戻り値
変数`r`のアドレスを返す。


##例外
投げない


##例
```cpp
#include <memory>
#include <iostream>

struct useless_type {};

// operator&がオーバーロードされたクラス
class nonaddressable {
public:
  useless_type operator&() const { return useless_type(); }
};

int main()
{
  {
    int x = 3;
    int* p1 = std::addressof(x); // OK : アドレス取得できる
    int* p2 = &x; // OK : アドレス取得できる
  }
  {
    nonaddressable x;
    nonaddressable* p1 = std::addressof(x); // OK : アドレス取得できる
//  nonaddressable* p2 = &x; // エラー！アドレス取得できない
  }
}
```
* addressof[color ff0000]

###出力
```
```

##バージョン
###言語
- C++11

###処理系
- [Clang](/implementation.md#clang): ??
- [GCC](/implementation.md#gcc): 
- [GCC, C++0x mode](/implementation.md#gcc): 4.7.0
- [ICC](/implementation.md#icc): ??
- [Visual C++](/implementation.md#visual_cpp): 11.0, 12.0
	- Visual C++ 11.0はマニュアル（MSDNライブラリ）に記載がないものの、実装されている。

##参照
[boost::addressof() - Boost C++ Libraries](http://www.boost.org/doc/libs/release/libs/utility/utility.htm#addressof)

