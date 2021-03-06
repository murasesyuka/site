#stddev (C++11)
* random[meta header]
* std[meta namespace]
* normal_distribution[meta class]
* function[meta id-type]

```cpp
result_type stddev() const;
```

##概要
生成する範囲の標準偏差を取得する。


##戻り値
構築時に設定された、値の範囲の標準偏差を返す。


##例
```cpp
#include <iostream>
#include <random>

int main()
{
  std::normal_distribution<> dist(0.0, 1.0);

  double stddev = dist.stddev();
  std::cout << stddev << std::endl;
}
```

###出力
```
1
```

##バージョン
###言語
- C++11

###処理系
- [Clang](/implementation.md#clang): ??
- [GCC](/implementation.md#gcc): 
- [GCC, C++0x mode](/implementation.md#gcc): 4.7.2
- [ICC](/implementation.md#icc): ??
- [Visual C++](/implementation.md#visual_cpp) ??


##参照


