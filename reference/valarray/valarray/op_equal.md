#operator==
* valarray[meta header]
* std[meta namespace]
* function[meta id-type]

```cpp
namespace std {
  template <class T>
  valarray<bool> operator==(const valarray<T>& xs, const valarray<T>& ys); // (1)

  template <class T>
  valarray<bool> operator==(const valarray<T>& xs, const T& y);            // (2)

  template <class T>
  valarray<bool> operator==(const T& x, const valarray<T>& ys);            // (3)
}
```

##概要
`valarray`において、左辺と右辺を等値比較する。


- (1) : `xs`の各要素と、`ys`の各要素が等値かを判定する。
- (2) : `xs`の各要素と、`y`が等値かを判定する。
- (3) : `ys`の各要素と、`x`が等値かを判定する。


##戻り値

- (1) : 以下のコードと同等のことを行う：

```cpp
valarray<bool> result(xs.size());
for (size_t i = 0; i < result.size(); ++i) {
  result[i] = xs[i] == ys[i];
}
return result;
```


- (2) : 以下のコードと同等のことを行う：

```cpp
valarray<bool> result(xs.size());
for (size_t i = 0; i < result.size(); ++i) {
  result[i] = xs[i] == y;
}
return result;
```


- (3) : 以下のコードと同等のことを行う：

```cpp
valarray<bool> result(ys.size());
for (size_t i = 0; i < result.size(); ++i) {
  result[i] = x == ys[i];
}
return result;
```


##備考
2つの`valarray`オブジェクトの要素数が異なる場合、その挙動は未定義。


##例
```cpp
#include <cassert>
#include <valarray>
#include <algorithm>

void expect_all_true(const std::valarray<bool>& v)
{
  assert((std::all_of(std::begin(v), std::end(v), [](bool b) { return b; })));
}

int main()
{
  const std::valarray<int> a = {1, 2, 3};
  const std::valarray<int> b = {1, 2, 3};
  const std::valarray<int> c = {1, 1, 1};

  const std::valarray<bool> result1 = a == b;
  expect_all_true(result1);

  const std::valarray<bool> result2 = c == 1;
  expect_all_true(result2);

  const std::valarray<bool> result3 = 1 == c;
  expect_all_true(result3);
}
```

###出力
```
```


