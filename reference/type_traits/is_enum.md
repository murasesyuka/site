#is_enum (C++11)
* type_traits[meta header]
* std[meta namespace]
* class template[meta id-type]

```cpp
namespace std {
  template <class T>
  struct is_enum;
}
```

##概要
型`T`が列挙型かを調べる


##効果
`is_enum`は、型`T`が列挙型であるならば[`true_type`](./integral_constant-true_type-false_type.md)から派生し、そうでなければ[`false_type`](./integral_constant-true_type-false_type.md)から派生する。


##例
```cpp
#include <type_traits>

enum e {};
enum class ec {};

static_assert(std::is_enum<e>::value == true, "value == true, e is enum");
static_assert(std::is_same<std::is_enum<e>::value_type, bool>::value, "value_type == bool");
static_assert(std::is_same<std::is_enum<e>::type, std::true_type>::value, "type == true_type");
static_assert(std::is_enum<e>() == true, "is_enum<e>() == true");

static_assert(std::is_enum<int>::value == false, "value == false, int is not enum");
static_assert(std::is_same<std::is_enum<int>::value_type, bool>::value, "value_type == bool");
static_assert(std::is_same<std::is_enum<int>::type, std::false_type>::value, "type == false_type");
static_assert(std::is_enum<int>() == false, "is_enum<int>() == false");

static_assert(std::is_enum<const e>::value == true, "const e is enum");
static_assert(std::is_enum<volatile e>::value == true, "volatile e is enum");
static_assert(std::is_enum<const volatile e>::value == true, "const volatile e is enum");
static_assert(std::is_enum<ec>::value == true, "ec is enum");

static_assert(std::is_enum<e*>::value == false, "e* is not enum");
static_assert(std::is_enum<e&>::value == false, "e& is not enum");
static_assert(std::is_enum<e ()>::value == false, "e () is not enum");
static_assert(std::is_enum<e [1]>::value == false, "e [1] is not enum");

int main(){}
```

###出力
```cpp
```

##バージョン
###言語
- C++11

###処理系
- [GCC, C++0x mode](/implementation.md#gcc): 4.3.4, 4.5.3, 4.6.1, 4.7.0
- [Visual C++](/implementation.md#visual_cpp) 10.0

####備考
上の例でコンパイラによってはエラーになる。GCC 4.3.4, 4.5.3, Visual C++ 10.0 は [`integral_constant`](./integral_constant-true_type-false_type.md) が `operator bool` を持っていないためエラーになる。また、GCC 4.3.4 および Visual C++ 10.0 は `enum class` に対応していないためエラーになる。

