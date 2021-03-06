#atan
* cmath[meta header]
* std[meta namespace]
* function[meta id-type]
* [mathjax enable]

```cpp
namespace std {
  float atan(float x);

  double atan(double x);

  long double atan(long double x);

  double atan(Integral x);   // C++11
}
```
* Integral[italic]

##概要
算術型の逆正接（アークタンジェント、arc tangent）を求める。


##戻り値
引数 `x` の逆正接を `[-π/2; π/2]` の範囲で返す。


##備考
$$ f(x) = \tan^{-1} x $$


##例
```cpp
#include <cmath>
#include <iostream>

int main() {
  static const double pi = 3.14159265358979265358979;
  std::cout << std::fixed;
  std::cout << "atan(0.0)   = " << std::atan(0.0) << std::endl;
  std::cout << "atan(0.5)   = " << std::atan(0.5) << std::endl;
  std::cout << "atan(1/√2) = " << std::atan(1/std::sqrt(2)) << std::endl;
  std::cout << "atan(√3/2) = " << std::atan(std::sqrt(3)/2) << std::endl;
  std::cout << "atan(1.0)   = " << std::atan(1.0) << std::endl;
  std::cout << "atan(∞)    = " << std::atan(INFINITY) << std::endl;
}
```

###出力
```
atan(0.0)   = 0.000000
atan(0.5)   = 0.463648
atan(1/√2) = 0.615480
atan(√3/2) = 0.713724
atan(1.0)   = 0.785398
atan(∞)    = 1.570796
```

##バージョン
###言語
- C++03
- C++11

###処理系
- [Clang](/implementation.md#clang): 1.9, 2.9, 3.1
- [GCC](/implementation.md#gcc): 3.4.6, 4.2.4, 4.3.5, 4.4.5, 4.5.1, 4.5.2, 4.6.1, 4.7.0
- [GCC, C++0x mode](/implementation.md#gcc): 4.3.4, 4.4.5, 4.5.2, 4.6.1, 4.7.0
- [ICC](/implementation.md#icc): 10.1, 11.0, 11.1, 12.0
- [Visual C++](/implementation.md#visual_cpp) 7.1, 8.0, 9.0, 10.0

####備考
特定の環境で `constexpr` 指定されている場合がある。（独自拡張）
- GCC 4.6.1 以上


##実装例
マクローリン展開によって近似的に求めることができる。

$$ \tan^{-1} x = \sum_{n = 0}^{\infty} \frac{(-1)^n}{2n + 1} x^{2n + 1} \quad \mathrm{for} \; |x| < 1 $$


$ |x| \ge 1 $ の範囲、および $ |x| \rightarrow 1 $ 近傍の精度低下する領域においては、以下の公式による変換で求めることができる。

（特に $ \sqrt{2} + 1 < |x| $ の場合）

$$ \tan^{-1} x = \frac{\pi}{2} - \tan^{-1} \frac{1}{x} \quad \mathrm{for~all} \; x $$


（特に $ \sqrt{2} - 1 < |x| \le \sqrt{2} + 1 $ の場合）

$$ \tan^{-1} x = \frac{\pi}{4} + \tan^{-1} \frac{x - 1}{x + 1} \quad \mathrm{for~all} \; x $$
