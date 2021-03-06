#copy_n (C++11)
* algorithm[meta header]
* std[meta namespace]
* function template[meta id-type]


```cpp
namespace std {
  template <class InputIterator, class Size, class OutputIterator>
  OutputIterator copy_n(InputIterator first, Size n, OutputIterator result);
}
```

##概要
指定された数の要素をコピーする。


##効果
0 以上 `n` 未満であるそれぞれの `i` について、`*(result + i) = *(first + i)` を行う。


##戻り値
`result + n`


##計算量
正確に `n` 回代入が行われる。


##例
```cpp
#include <algorithm>
#include <iostream>
#include <iterator>
#include <vector>
 
int main() {
  std::vector<int> v = { 3, 1, 5, 2, 4 };
  std::copy_n(v.begin(), 5, std::ostream_iterator<int>(std::cout, "\n"));
}
```
* copy_n[color ff0000]

###出力
```
3
1
5
2
4
```


##実装例
```cpp
template<class InputIterator, class Size, class OutputIterator>
OutputIterator copy_n(InputIterator first, Size n, OutputIterator result) {
  for (Size i = 0; i < n; i++)
    *result++ = *first++;
  return result;
}
```

##バージョン
###言語
- C++11

###処理系
- [Clang](/implementation.md#clang): 3.0
- [GCC](/implementation.md#gcc): 
- [GCC, C++0x mode](/implementation.md#gcc): 4.4.7
- [ICC](/implementation.md#icc): ??
- [Visual C++](/implementation.md#visual_cpp): ??


