#seed_seq (C++11)
* random[meta header]
* std[meta namespace]
* class template[meta id-type]

```cpp
namespace std {
  class seed_seq;
}
```

##概要
`seed_seq`クラスは、擬似乱数を生成するためのシード列を表現するためのクラスである。  
シード列は、32ビット整数の[`vector`](/reference/vector.md)として表現される。

擬似乱数は一つの値をシードとして使用することもできるが、より多くの乱雑さ(エントロピー)が必要な場合に、複数のシードで擬似乱数を初期化するためにこのクラスを使用する。


##メンバ関数
###構築

| 名前 | 説明 | 対応バージョン |
|----------------------------------------------|----------------------|-------|
| [`(constructor)`](./seed_seq/op_constructor.md) | コンストラクタ       | C++11 |
| `~seed_seq() = default;`                     | デストラクタ         | C++11 |
| `void operator()(const seed_seq&) = delete;` | 代入演算子。代入不可 | C++11 |


###生成

| 名前 | 説明 | 対応バージョン |
|--------------------------------------|--------------------|-------|
| [`generate`](./seed_seq/generate.md) | シード列を生成する | C++11 |


##特性

| 名前 | 説明 | 対応バージョン |
|--------------------------------|----------------------------|-------|
| [`size`](./seed_seq/size.md)   | シード列の要素数を取得する | C++11 |
| [`param`](./seed_seq/param.md) | シード列を取得する         | C++11 |


##メンバ型

| 型 | 説明 | 対応バージョン |
|---------------|-------------------|-------|
| `result_type` | シードを表す整数型 [`uint_least32_t`](/reference/cstdint/uint_least32_t.md)。 | C++11 |


##例
以下は、メルセンヌ・ツイスター法による擬似乱数生成器を、状態シーケンスのサイズ分のシード列で初期化する例である。

```cpp
#include <iostream>
#include <array>
#include <algorithm> // generate
#include <functional> // ref
#include <random>

int main()
{
  // 擬似乱数生成器の状態シーケンスのサイズ分、
  // シードを用意する
  std::array<
    std::seed_seq::result_type,
    std::mt19937::state_size
  > seed_data;

  // 非決定的な乱数でシード列を構築する
  std::random_device seed_gen;
  std::generate(seed_data.begin(), seed_data.end(), std::ref(seed_gen));

  std::seed_seq seq(seed_data.begin(), seed_data.end());

  // 擬似乱数生成器をシード列で初期化
  std::mt19937 engine(seq);

  // 乱数生成
  for (int i = 0; i < 10; ++i) {
    std::uint32_t result = engine();
    std::cout << result << std::endl;
  }
}
```

###出力
```
2454004218
3605965574
154830518
2773897806
2068951439
2231513109
607824
726899798
1108321733
2723491878
```

##バージョン
###言語
- C++11

###処理系
- [Clang](/implementation.md#clang): ??
- [GCC](/implementation.md#gcc): 
- [GCC, C++0x mode](/implementation.md#gcc): 4.7.2
- [ICC](/implementation.md#icc): ??
- [Visual C++](/implementation.md#visual_cpp): ??

##参照
* [Does std::mt19937 require warmup? - StackOverflow](http://stackoverflow.com/questions/15509270/does-stdmt19937-require-warmup)
* [Mersenne twister warm up vs. reproducibility](http://stackoverflow.com/questions/16078794/mersenne-twister-warm-up-vs-reproducibility)

