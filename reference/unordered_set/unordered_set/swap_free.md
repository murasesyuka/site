#swap (非メンバ関数) (C++11)
* unordered_set[meta header]
* std[meta namespace]
* function[meta id-type]

```cpp
namespace std {
  template <class Key, class Hash, class Pred, class Alloc>
  void swap(unordered_set<Key, Hash, Pred, Alloc>& x,
            unordered_set<Key, Hash, Pred, Alloc>& y);
}
```

##概要
2 つの `unordered_set` オブジェクトの内容を入れ替える。


##効果
`x.`[`swap`](./swap.md)`(y)` と同等。


##戻り値
なし


##例
```cpp
#include <iostream>
#include <string>
#include <unordered_set>
#include <iterator>
#include <algorithm>

template <class C>
void print(const std::string& label, const C& c, std::ostream& os = std::cout)
{
  os << label << ":";
  std::copy(std::begin(c), std::end(c), std::ostream_iterator<typename C::value_type>(os, ", "));
  os << std::endl;
}

int main()
{
  std::unordered_set<int> us1{ 1, 2, 3, };
  std::unordered_set<int> us2{ 4, 5, 6, };

  print("us1 before", us1);
  print("us2 before", us2);
  swap(us1, us2);
  print("us1 after", us1);
  print("us2 after", us2);
}
```
* iostream[link /reference/iostream.md]
* string[link /reference/string.md]
* unordered_set[link /reference/unordered_set.md]
* iterator[link /reference/iterator.md]
* algorithm[link /reference/algorithm.md]
* ostream[link /reference/ostream.md]
* copy[link /reference/algorithm/copy.md]
* begin[link /reference/iterator/begin.md]
* end[link /reference/iterator/end.md]
* ostream_iterator[link /reference/iterator/ostream_iterator.md]

###出力
```
us1 before:3, 2, 1,
us2 before:6, 5, 4,
us1 after:6, 5, 4,
us2 after:3, 2, 1,
```

注：[`unordered_set`](/reference/unordered_set/unordered_set.md) は非順序連想コンテナであるため、出力順序は無意味であることに注意


##バージョン
###言語
- C++11

###処理系
- [Clang](/implementation.md#clang): -
- [Clang, C++0x mode](/implementation.md#clang): 3.1
- [GCC](/implementation.md#gcc): -
- [GCC, C++0x mode](/implementation.md#gcc): 4.7.0
- [ICC](/implementation.md#icc): ?
- [Visual C++](/implementation.md#visual_cpp) ?

##実装例
```cpp
namespace std {
  template <class Key, class Hash, class Pred, class Alloc>
  void swap(unordered_set<Key, Hash, Pred, Alloc>& x,
            unordered_set<Key, Hash, Pred, Alloc>& y)
  {
    x.swap(y);
  }
}
```
* swap[link ./swap.md]

##参照

| | |
|----------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------|
| [`swap`](./swap.md) | 内容の交換（メンバ関数） |
| [`operator=`](./op_assign.md) | 代入演算子 |
| [`operator==`](./op_equal.md) | 等値比較 |
| [`operator!=`](./op_not_equal.md) | 非等値比較 |

