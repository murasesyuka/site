#is_final (C++14)
* type_traits[meta header]
* std[meta namespace]
* class template[meta id-type]

```cpp
namespace std {
  template <class T>
  struct is_final;
}
```

##概要
型に`final`が付いているかを調べる。


##要件
型`T`がクラス型である場合、その型は完全型でなければならない。


##効果
`is_final`は、型`T`が`final`指定されていれば[`true_type`](./integral_constant-true_type-false_type.md)から派生し、そうでなければ[`false_type`](./integral_constant-true_type-false_type.md)から派生する。

「これ以上継承できない場合は`true_type`」ではなく`final`識別子の有無で判断することに注意。`int`のような組み込み型は、継承はできないが`false_type`となる。


##備考
この型特性は、EBCO(empty-base-class optimization)のために使用できる。


##例
```cpp
#include <type_traits>

struct A {};
struct B final {};

static_assert(std::is_final<A>::value == false, "A is a not final class");
static_assert(std::is_final<B>::value == true,  "B is a final class");
static_assert(std::is_final<int>::value == false, "int is a not final class");

int main(){}
```

###出力
```
```

##バージョン
###言語
- C++14

###処理系
- [Clang, C++14 mode](/implementation.md#clang): 3.5
- [GCC, C++0x mode](/implementation.md#gcc): 5.0
- [Visual C++](/implementation.md#visual_cpp): ??


##参照
- [LWG issue 2112. User-defined classes that cannot be derived from](http://www.open-std.org/jtc1/sc22/wg21/docs/lwg-defects.html#2112)

