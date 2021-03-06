#remove_volatile (C++11)
* type_traits[meta header]
* std[meta namespace]
* class template[meta id-type]

```cpp
namespace std {
  template <class T>
  struct remove_volatile {
    typedef … type;
  };

  template <class T>
  using remove_volatile_t = typename remove_volatile<T>::type; // C++14
}
```

##概要
型の`volatile`修飾を除去する。


##効果
`remove_volatile`は、型`T`に含まれる最上位の`volatile`修飾を除去した型を、メンバ型`type`として定義する。


##例
```cpp
#include <type_traits>

static_assert(std::is_same<
        std::remove_volatile<volatile int>::type,
        int
    >::value,
    "transform from volatile int to int");

static_assert(std::is_same<
        std::remove_volatile<volatile int&>::type,
        volatile int&
    >::value,
    "transform from volatile int& to volatile int&");

static_assert(std::is_same<
        std::remove_volatile<volatile int*>::type,
        volatile int*
    >::value,
    "transform from volatile int* to volatile int*");

static_assert(std::is_same<
        std::remove_volatile<int* volatile>::type,
        int*
    >::value,
    "transform from int* volatile to int*");

int main() {}
```

###出力
```
```

##バージョン
###言語
- C++11

###処理系
- [Clang](/implementation.md#clang): 3.0
- [GCC, C++0x mode](/implementation.md#gcc): 4.3.6
- [Visual C++](/implementation.md#visual_cpp): ??


##参照
- [N3546 TransformationTraits Redux](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3546.pdf)
- [N3655 TransformationTraits Redux, v2](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3655.pdf)

