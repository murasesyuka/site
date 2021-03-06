#crend (C++11)
* map[meta header]
* std[meta namespace]
* multimap[meta class]
* function[meta id-type]

```cpp
const_reverse_iterator crend() const noexcept;
```


##概要
`multimap` コンテナの先頭要素の前（これは反転シーケンスの末尾にあたる）を指す逆イテレータを返す。 
`crend()` は [`begin()`](/reference/map/multimap/begin.md) と同じ要素を指すわけではなく、その前の要素を指すことに注意。


##戻り値
反転シーケンスの終端を指す逆イテレータ。 
`reverse_iterator` と `const_reverse_iterator` はメンバ型である。`multimap` クラステンプレートにおいて、これらは逆双方向イテレータであり、それぞれ `reverse_iterator<iterator>`, `reverse_iterator<const_iterator>` と定義される。


##例
```cpp
#include <iostream>
#include <map>

int main()
{
  std::multimap<int, char> c;
  c.insert(std::make_pair(5, 'e'));
  c.insert(std::make_pair(2, 'b'));
  c.insert(std::make_pair(4, 'd'));
  c.insert(std::make_pair(1, 'a'));
  c.insert(std::make_pair(1, 'a'));

  std::multimap<int,char>::const_reverse_iterator i = c.crbegin();
  for( ; i != c.crend() ; ++i )
    std::cout << i->first << " " << i->second << std::endl;

  return 0;
}
```


###出力
```
5 e
4 d
2 b
1 a
1 a
```

###処理系
- [Clang](/implementation.md#clang): ??
- [GCC](/implementation.md#gcc): ??
- [GCC, C++11 mode](/implementation.md#gcc): ??
- [ICC](/implementation.md#icc): ??
- [Visual C++](/implementation.md#visual_cpp): ??, 11.0



##参照

| 名前 | 説明 |
|------------------------------------------------------------------------------------------------|--------------------------------------------|
| [`multimap::begin`](/reference/map/multimap/begin.md) | 先頭を指すイテレータを取得する |
| [`multimap::end`](/reference/map/multimap/end.md) | 末尾を指すイテレータを取得する |
| [`multimap::cbegin`](/reference/map/multimap/cbegin.md) | 先頭を指すconstイテレータを取得する |
| [`multimap::cend`](/reference/map/multimap/cend.md) | 末尾を指すconstイテレータを取得する |
| [`multimap::rbegin`](/reference/map/multimap/rbegin.md) | 末尾を指す逆イテレータを取得する |
| [`multimap::rend`](/reference/map/multimap/rend.md) | 先頭を指す逆イテレータを取得する |
| [`multimap::crbegin`](/reference/map/multimap/rbegin.md) | 末尾を指す逆constイテレータを取得する |
