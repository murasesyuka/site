#operator!=
* map[meta header]
* std[meta namespace]
* function[meta id-type]

```cpp
namespace std {
  template <class Key, class T, class Compare, class Allocator>
  bool operator!=(const map<Key,T,Compare,Allocator>& x, const map<Key,T,Compare,Allocator>& y);
}
```

##概要
`x` と `y` が等しくないかどうかの判定を行う。


##パラメータ
- `x`, `y`<br/>
比較するコンテナ。


##戻り値
二つのコンテナが等しくない場合に `true`, そうでない場合に `false`。


##計算量
[`size()`](/reference/map/map/size.md) に対して線形時間。


##例
```cpp
#include <iostream>
#include <map>

int main()
{
  std::map<int,char> s1, s2;
  s1.insert(std::make_pair(1,'a'));
  s1.insert(std::make_pair(2,'b'));
  s1.insert(std::make_pair(3,'c'));
  s2 = s1;

  std::cout << (s1 != s2) << std::endl;

  s2.insert(std::make_pair(4,'d'));

  std::cout << (s1 != s2) << std::endl;

  return 0;
}
```

###出力
```
0
1
```

###処理系
- [Clang](/implementation.md#clang): ??
- [GCC](/implementation.md#gcc): ??
- [GCC, C++11 mode](/implementation.md#gcc): ??
- [ICC](/implementation.md#icc): ??
- [Visual C++](/implementation.md#visual_cpp): ??, 11.0

