#stold (C++11)
```cpp
namespace std {
  double stold(const string& str, size_t* idx = nullptr);
  long double stold(const wstring& str, size_t* idx = nullptr);
}
```

##概要
文字列`str`を数値として読み取って、`long double`型の値に変換する。

##効果
それぞれ`std::strtod(str.c_str(), &end)`および`std::wcstold(str.c_str(), &end)`を呼び出して、その戻り値を返す。

idxが非nullptrの場合、変換に使用されなかった要素のインデックス（`end - str.c_str()`）が格納される。

##戻り値
変換して得られた数値が返される。

##例外
- 数値への変換が行われなかった場合、`std::invalid_argument`が送出される。
- 結果が範囲外の値になった場合（`errno`が`ERANGE`となった場合）、`std::out_of_range`が送出される。

##備考
### errnoの扱い
- Visual C++ 11やGCC (libstdc++) 4.8.2では、この関数を呼び出すと`errno`の値が変更される。
- Clang (libc++) 3.3では、この関数の呼び出し前後で`errno`の値は変化しない。

### グローバルロケールの影響
この関数は、`setlocale`関数により挙動が変化する。

- `strtold`関数での文字列先頭の空白を読み飛ばす処理に、`<cctype>`の`isspace`関数が使用される。
- 小数点記号はLC_NUMERICで指定されたものが使用される。

##例
```cpp
#include <iostream>
#include <string>

int main()
{
  // 十進法での変換
  std::cout << "---- decimal point" << std::endl;

  long double a = std::stold("1.5"); // std::stold("1.5", nullptr);
  std::cout << a << std::endl;

  long double aw = std::stold(L"1."); // std::stold(L"1.", nullptr);
  std::cout << aw << std::endl;

  // 指数表記の変換
  std::cout << "---- base = 8" << std::endl;

  long double b = std::stold("0.5e3", nullptr);
  std::cout << b << std::endl;

  long double bw = std::stold(L".25e3", nullptr);
  std::cout << bw << std::endl;

  // 十六進法での変換
  std::cout << "---- base = 16" << std::endl;

  long double c = std::stold("0x1.2P3", nullptr);
  std::cout << c << std::endl;

  long double cw = std::stold(L"0x1.2P4", nullptr);
  std::cout << cw << std::endl;

  // 2番目の仮引数の使用例
  std::cout << "---- use of idx parameter" << std::endl;

  std::string es = "30.75%";
  std::size_t ei;
  long double e = std::stold(es, &ei);
  std::cout << e << ' ' << es[ei] << std::endl;

  std::wstring ews = L"32%";
  std::size_t ewi;
  long double ew = std::stold(ews, &ewi);
  std::cout << ew << ' ' << ewi << std::endl;

  // 文字列先頭に空白がある場合
  std::cout << "---- space character before number" << std::endl;
  std::cout << std::stold("    -1") << std::endl;
  std::cout << std::stold(L"    -.25") << std::endl;
}
```

###出力例
```
1.5
1
500
250
---- base = 16
9
18
---- use of idx parameter
30.75 %
32 2
---- space character before number
-1
-0.25
```

##実装例
```cpp
long double stold(const string& str, size_t* idx = nullptr) {
  const char* p = str.c_str();
  char* end;
  long double x = strtold(p, &end);
  if (p == end) {
    throw invalid_argument("stold");
  }
  if (errno == ERANGE) {
    throw out_of_range("stold");
  }
  if (idx != nullptr) {
    *idx = static_cast<std::size_t>(end - p);
  }
  return x;
}

long double stold(const wstring& str, size_t* idx = nullptr) {
  const wchar_t* p = str.c_str();
  wchar_t* end;
  long double x = wcstold(p, &end);
  if (p == end) {
    throw invalid_argument("stold");
  }
  if (errno == ERANGE) {
    throw out_of_range("stold");
  }
  if (idx != nullptr) {
    *idx = static_cast<std::size_t>(end - p);
  }
  return x;
}
```

##バージョン
###言語
- C++11

###処理系
- [Clang](/implementation#clang.md): ?
- [GCC](/implementation#gcc.md): ?
- [GCC, C++11 mode](/implementation#gcc.md): ?
- [ICC](/implementation#icc.md): ?
- [Visual C++](/implementation#visual_cpp.md): 10.0, 11.0, 12.0

ただし、Visual C++ 10.0, 11.0は十六進法に対応していない（12.0は未確認）。

##参照
### C標準ライブラリに由来する関数
- `atof`: `stold`は`atof`を`std::string`および`std::wsting`に対応させ、戻り値の型を`long double`に変更したものと見なせる。
- `strtold`, `wcstold`: `stold`は`strtold`および`wcstold`をそれぞれ`std::string`と`std::wsting`に対応させたものと見なせる。

### ファミリー
- [`stoi`](./stoi.md): 戻り値の型が`int`となったもの。
- [`stol`](./stol.md): 戻り値の型が`long`となったもの。
- [`stoll`](./stoll.md): 戻り値の型が`long long`となったもの。
- [`stoul`](./stoul.md): 戻り値の型が`unsgined long`となったもの。
- [`stoull`](./stoull.md): 戻り値の型が`unsgined long long`となったもの。
- [`stof`](./stof.md): 戻り値の型が`float`となったもの。
- [`stod`](./stod.md): 戻り値の型が`double`となったもの。
- (`stold`: この関数自身)