#operator>=
* set[meta header]
* std[meta namespace]
* function[meta id-type]

```cpp
namespace std {
  template <class Key, class Compare, class Allocator>
  bool operator>=(const set<Key,Compare,Allocator>& x, const set<Key,Compare,Allocator>& y);
}
```

##概要
`x` が `y` より大きいか等しいかの判定を行う。


##引数
- `x`, `y`<br/>
比較するコンテナ。


##戻り値
`x` が `y` より大きいか等しい場合に `true`, そうでない場合に `false`。


##計算量
[`size`](./size.md)`()` に対して線形時間。


##例
```cpp
#include <iostream>
#include <set>

int main()
{
  std::set<int> s1, s2;
  s1.insert(10);
  s1.insert(20);
  s1.insert(30);
  s2 = s1;

  std::cout << (s1 >= s2) << std::endl;

  s2.insert(40);

  std::cout << (s1 >= s2) << std::endl;
}
```
* iostream[link ../../iostream.md]
* set[link ../../set.md]
* insert[link insert.md]
* cout[link ../../iostream/cout.md]
* endl[link ../../ostream/endl.md]
* >=[color ff0000]

###出力
```
1
0
```
