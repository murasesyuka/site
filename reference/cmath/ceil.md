#ceil
* cmath[meta header]
* std[meta namespace]
* function[meta id-type]

```cpp
namespace std {
  float ceil(float x);

  double ceil(double x);

  long double ceil(long double x);

  double ceil(Integral x);			// C++11 から
}
```
* Integral[italic]

##概要
引数 `x` 以上で最小の整数値を得る。


##戻り値
引数 `x` 以上で最小の整数値


##備考
- 本関数は、C99 の規格にある `ceil`（より正確には `math.h` ヘッダの `ceil`、`ceilf`、`ceill` の 3 つ。それぞれ C++ の `double`、`float`、`long double` バージョンに相当）と同等である。  
	C99 では、処理系が ISO IEC 60559（IEEE 754 と同一)に準拠している場合、以下のように規定されている。

	- `x = ±0` の場合、`±0` を返す。
	- `x = ±∞` の場合、`±∞` を返す。

	また、本関数は、丸めモードが `FE_UPWARD` に設定されている時の [`rint`](rint.md)、あるいは [`nearbyint`](nearbyint.md) のいずれかと同等である旨の記載がある。
	したがって、本関数において戻り値が引数 `x` と異なる場合に例外 `FE_INEXACT` が発生するか否かは実装依存であるものと思われる。

- 処理系が ISO IEC 60599 に準拠しているかどうかは、C99 の場合はマクロ `__STDC_IEC_599__` が `1` に定義されている事で判別可能であるが、C++ 規格書には該当する記載を見つけることができなかった。


##例
```cpp
#include <cfenv>
#include <cmath>
#include <iostream>

void test(double x)
{
  std::feclearexcept(FE_ALL_EXCEPT);
  std::cout << "ceil(" << x << ") = " << std::ceil(x) << std::endl;
  std::cout << "FE_INEXACT = " << std::boolalpha << (std::fetestexcept(FE_INEXACT) != 0) << std::endl << std::endl;
}

int main()
{
  test(2.0);
  test(2.1);
  test(2.5);
  test(2.9);
  test(-2.0);
  test(-2.1);
  test(-2.5);
  test(-2.9);
}
```
* iostream[link ../iostream.md]
* cmath[link ../cmath.md]
* cfenv[link ../cfenv.md.nolink]
* ceil[color ff0000]
* cout[link ../iostream/cout.md]
* endl[link ../ostream/endl.md]
* boolalpha[link ../ios/boolalpha.md]
* FE_INEXACT[link ../cfenv/FE_INEXACT.md.nolink]
* FE_ALL_EXCEPT[link ../cfenv/FE_ALL_EXCEPT.md.nolink]
* feclearexcept[link ../cfenv/feclearexcept.md.nolink]
* fetestexcept[link ../cfenv/fetestexcept.md.nolink]

###出力例
```
ceil(2) = 2
FE_INEXACT = false

ceil(2.1) = 3
FE_INEXACT = true

ceil(2.5) = 3
FE_INEXACT = true

ceil(2.9) = 3
FE_INEXACT = true

ceil(-2) = -2
FE_INEXACT = false

ceil(-2.1) = -2
FE_INEXACT = true

ceil(-2.5) = -2
FE_INEXACT = true

ceil(-2.9) = -2
FE_INEXACT = true

```

引数と結果が異なる場合に例外 `FE_INEXACT` が発生するか否かは実装によって異なる可能性がある。
