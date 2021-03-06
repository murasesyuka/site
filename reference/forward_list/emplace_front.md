#emplace_front (C++11)
* forward_list[meta header]
* std[meta namespace]
* forward_list[meta class]
* function[meta id-type]

```cpp
template <class... Args>
void emplace_front(Args&&... args);
```

##概要
直接構築で新たな要素を先頭に追加する。  
この関数の引数`args...`は、要素型`T`のコンストラクタ引数である。当関数の内部で要素型`T`のコンストラクタを呼び出し、追加する要素を構築する。


##戻り値
なし


##計算量
定数時間


##例
```cpp
#include <iostream>
#include <forward_list>
#include <utility>
#include <string>
#include <algorithm>

int main()
{
  std::forward_list<std::pair<int, std::string>> ls;

  ls.emplace_front(1, std::string("world"));
  ls.push_front(std::make_pair(3, std::string("hello")));

  std::for_each(ls.begin(), ls.end(), [](decltype(ls)::const_reference x) {
    std::cout << x.first << ',' << x.second << std::endl;
  });
}
```
* emplace_front[color ff0000]

###出力
```
3,hello
1,world
```

##バージョン
###言語
- C++11

###処理系
- [Clang](/implementation.md#clang): ??
- [GCC](/implementation.md#gcc): 
- [GCC, C++0x mode](/implementation.md#gcc): 4.7.0
- [ICC](/implementation.md#icc): ??
- [Visual C++](/implementation.md#visual_cpp) ??


##参照


