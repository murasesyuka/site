#shift
```cpp
valarray<T> shift(int n) const;
```

##概要
要素の位置をシフトする。


##戻り値
- `n`が正の値である場合、`n`個分だけ要素を前(`0`番目に向かう方向)に移動する。
- `n`が負の値である場合、`n`個分だけ要素を後ろ(`size()`に向かう方向)に移動する。

移動したことによって範囲外になった要素の値はなくなる。移動したことによって使用されなくなった要素の値は`0`で埋められる。


##例
```cpp
#include <iostream>
#include <valarray>

template <class T>
void print(const char* name, const std::valarray<T>& v)
{
  std::cout << name << " : {";
  bool first = true;

  for (const T& x : v) {
    if (first) {
      first = false;
    }
    else {
      std::cout << ',';
    }
    std::cout << x;
  }
  std::cout << "}" << std::endl;
}

int main()
{
  const std::valarray<int> v = {1, 2, 3, 4, 5};

  const std::valarray<int> left_shift_result = v.shift(3);
  print("left_shift_result", left_shift_result);

  const std::valarray<int> right_shift_result = v.shift(-3);
  print("right_shift_result", right_shift_result);
}
```

###出力
```
left_shift_result : {4,5,0,0,0}
right_shift_result : {0,0,0,1,2}
```

