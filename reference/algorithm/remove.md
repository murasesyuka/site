#remove
* algorithm[meta header]
* std[meta namespace]
* function template[meta id-type]

```cpp
namespace std {
  template <class ForwardIterator, class T>
  ForwardIterator remove(ForwardIterator first,
                         ForwardIterator last,
                         const T& value);
}
```

##概要
指定された要素を取り除く。


##要件
`*first` の型は `MoveAssignable` の要件を満たす必要がある


##効果
`[first,last)` 内にあるイテレータ `i` について、`*i == value` である要素を取り除き、有効な要素を範囲の前に寄せる。


##戻り値
有効な要素の末尾の次を指すイテレータを返す。


##計算量
正確に `last - first` 回の比較を行う


##注意
安定。


##備考
有効な要素を範囲の前方に集める処理には、ムーブを使用する。

取り除いた要素の先頭を指すイテレータを`ret`とし、範囲`[ret, last)`の各要素には、有効な要素からムーブされた値が設定される。それらの値は、「有効だが未規定な値」となる。


##例
```cpp
#include <algorithm>
#include <iostream>
#include <vector>
 
int main() {
  std::vector<int> v = { 2,3,1,2,1 };

  auto result = std::remove(v.begin(), v.end(), 1);

  // [v.begin(),result) の範囲に 1 を除去した結果が入っている
  std::for_each(v.begin(), result, [](int x) { std::cout << x << ","; });
  std::cout << std::endl;

  // remove を使ってもコンテナの要素数は変わらないことに注意しよう
  std::cout << "size before: " << v.size() << std::endl;

  // [v.begin(),result) の範囲に 1 を除去した結果が入っているので、
  // [result,v.end()) を erase することでサイズも変更することができる
  // （Erase-remove イディオム）
  v.erase(result, v.end());
  std::cout << "size after: " << v.size() << std::endl;
}
```
* result[color ff0000]
* remove[color ff0000]
* result[color ff0000]
* v.erase(result, v.end());[color ff0000]


###出力
```
2,3,2,
size before: 5
size after: 3
```


##実装例
```cpp
template <class ForwardIterator, class T>
ForwardIterator remove(ForwardIterator first, ForwardIterator last, const T& value) {
  auto result = first;
  for ( ; first != last; ++first)
    if (!(*first == value))
      *result++ = move(*first);
  return result;
}
```


##参照
- [LWG Issue 2110. `remove` can't swap but note says it might](http://www.open-std.org/jtc1/sc22/wg21/docs/lwg-defects.html#2110)
    - C++11までのこのアルゴリズムは、要素の移動にswap操作が行われるかもしれない、と書いていた。だが、このアルゴリズムの要件は`MoveAssignable`のみであるため、swapはできない。そのため、C++14からは、ムーブのみで要素の移動が行われるようになった。

