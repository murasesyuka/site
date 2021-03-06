#rbegin (C++14)
* iterator[meta header]
* std[meta namespace]
* function template[meta id-type]

```cpp
namespace std {
  template <class C>
  auto rbegin(C& c) -> decltype(c.rbegin());                 // (1)

  template <class C>
  auto rbegin(const C& c) -> decltype(c.rbegin());           // (2)

  template <class T, size_t N>
  reverse_iterator<T*> rbegin(T (&array)[N]);                // (3)

  template <class E>
  reverse_iterator<const E*> rbegin(initializer_list<E> il); // (4)
}
```
* reverse_iterator[link ./reverse_iterator.md]
* initializer_list[link /reference/initializer_list.md]

##概要
範囲の末尾を指す逆イテレータを取得する。

- (1) : コンテナの`rbegin()`メンバ関数で、範囲の末尾を指す、逆イテレータを返す。
- (2) : コンテナの`rbegin()`メンバ関数で、範囲の末尾を指す、読み取り専用逆イテレータを返す。
- (3) : 組み込み配列の末尾を指す、逆イテレータを返す。
- (4) : `initializer_list`オブジェクトの末尾を指す、読み取り専用逆イテレータを返す。


##戻り値
- (1) : `c.rbegin();`
- (2) : `c.rbegin();`
- (3) : [`reverse_iterator`](./reverse_iterator.md)`<T*>(array + N)`
- (4) : [`reverse_iterator`](./reverse_iterator.md)`<const E*>(`[`il.end()`](/reference/initializer_list/end.md)`)`


##例
```cpp
#include <iostream>
#include <vector>
#include <iterator>
#include <algorithm>

void print(int x)
{
  std::cout << x << " ";
}

int main()
{
  // コンテナ
  {
    std::vector<int> v = {1, 2, 3};

    decltype(v)::reverse_iterator first = std::rbegin(v);
    decltype(v)::reverse_iterator last = std::rend(v);

    std::for_each(first, last, print);
  }
  std::cout << std::endl;

  // 組み込み配列
  {
    int ar[] = {4, 5, 6};

    std::reverse_iterator<int*> first = std::rbegin(ar);
    std::reverse_iterator<int*> last = std::rend(ar);

    std::for_each(first, last, print);
  }
  std::cout << std::endl;

  // 初期化子リスト
  {
    std::initializer_list<int> init = {7, 8, 9};

    std::reverse_iterator<const int*> first = std::rbegin(init);
    std::reverse_iterator<const int*> last = std::rend(init);

    std::for_each(first, last, print);
  }
}
```
* rbegin[color ff0000]
* rend[link ./rend.md]
* std::reverse_iterator[link ./reverse_iterator.md]
* std::vector[link /reference/vector.md]
* std::for_each[link /reference/algorithm/for_each.md]
* std::cout[link /reference/iostream/cout.md]
* std::endl[link /reference/ostream/endl.md]

###出力
```
3 2 1 
6 5 4 
9 8 7 
```

##バージョン
###言語
- C++14

###処理系
- [Clang, C++14 mode](/implementation.md#clang): 3.4
- [GCC, C++14 mode](/implementation.md#gcc): 5.0
- [ICC](/implementation.md#icc): ??
- [Visual C++](/implementation.md#visual_cpp) ??


##参照
- [LWG Issue 2128. Absence of global functions `cbegin`/`cend`](http://www.open-std.org/jtc1/sc22/wg21/docs/lwg-defects.html#2128)

