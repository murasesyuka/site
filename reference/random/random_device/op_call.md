#operator()(C++11)
```cpp
result_type operator()();
```

##概要
非決定的な乱数の生成を行う。


##戻り値
実装定義な方法で、非決定的なランダム値を生成して返す。  
値の範囲は`[`[`min()`](./min.md), [`max()`](.max.md)`]`である。つまり、最小値と最大値両方を含む。


##例外
非決定的なランダム値を生成できなかった場合、[`exception`](/reference/exception/exception.md)から派生した実装定義の例外オブジェクトを送出する。


##例
```cpp
#include <iostream>
#include <random>

int main()
{
  std::random_device rd;

  for (int i = 0; i < 10; ++i) {
    // 乱数生成
    unsigned int result = rd();

    std::cout << result << std::endl;
  }
}
```


###出力例
```
2284556121
263670535
2150180423
108225722
1190313341
2571297678
2016112144
4255475211
252992055
1302323609
```

##バージョン
###言語
- C++11

###処理系
- [Clang](/implementation#clang.md): ??
- [GCC](/implementation#gcc.md): 
- [GCC, C++0x mode](/implementation#gcc.md): 4.7.2
- [ICC](/implementation#icc.md): ??
- [Visual C++](/implementation#visual_cpp.md) ??


##参照

