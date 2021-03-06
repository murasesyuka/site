#bucket_size (C++11)
* unordered_set[meta header]
* std[meta namespace]
* unordered_multiset[meta class]
* function[meta id-type]

```cpp
size_type bucket_size(size_type n) const;
```

##概要
インデックス（添え字）で指定したバケット内に格納されている要素の数を取得する。


##要件
パラメータ `n` は `[0, `[`bucket_count`](./bucket_count.md)`())` の範囲であること。


##戻り値
パラメータ `n`で指定した位置のバケット内に格納されている要素の数


##計算量
O(`bucket_size(n)`)


##例
```cpp
#include <iostream>
#include <string>
#include <unordered_set>
#include <algorithm>
#include <iterator>

int main()
{
  std::unordered_multiset<std::string> um{ "A", "B", "C", "D", "E", "A", "B", "C", "D", "E", };

  decltype(um)::size_type c = um.bucket_count();
  std::cout << "bucket_count() = " << c << std::endl;

  for (decltype(um)::size_type b = 0; b < c; ++b) {
    decltype(um)::size_type s = um.bucket_size(b);
    std::cout << "bucket = " << b << ", bucket_size = " << s << ", keys = { ";
    std::copy(um.cbegin(b), um.cend(b), std::ostream_iterator<std::string>(std::cout, ", "));
    std::cout << "}" << std::endl;
  }
}
```
* iostream[link /reference/iostream.md]
* string[link /reference/string.md]
* unordered_set[link /reference/unordered_set.md]
* algorithm[link /reference/algorithm.md]
* iterator[link /reference/iterator.md]
* unordered_multiset[link /reference/unordered_set/unordered_multiset.md]
* bucket_count[link /reference/unordered_set/unordered_multiset/bucket_count.md]
* copy[link /reference/algorithm/copy.md]
* cbegin[link /reference/unordered_set/unordered_multiset/cbegin-size_type.md]
* cend[link /reference/unordered_set/unordered_multiset/cend-size_type.md]
* ostream_iterator[link /reference/iterator/ostream_iterator.md]

###出力
```
bucket_count() = 11
bucket = 0, bucket_size = 0, keys = { }
bucket = 1, bucket_size = 0, keys = { }
bucket = 2, bucket_size = 0, keys = { }
bucket = 3, bucket_size = 0, keys = { }
bucket = 4, bucket_size = 0, keys = { }
bucket = 5, bucket_size = 6, keys = { A, A, C, C, D, D, }
bucket = 6, bucket_size = 2, keys = { E, E, }
bucket = 7, bucket_size = 2, keys = { B, B, }
bucket = 8, bucket_size = 0, keys = { }
bucket = 9, bucket_size = 0, keys = { }
bucket = 10, bucket_size = 0, keys = { }
```

##バージョン
###言語
- C++11

###処理系
- [Clang](/implementation.md#clang): -
- [Clang, C++0x mode](/implementation.md#clang): 3.1
- [GCC](/implementation.md#gcc): -
- [GCC, C++0x mode](/implementation.md#gcc): 4.7.2
- [ICC](/implementation.md#icc): ?
- [Visual C++:](/implementation.md#visual_cpp) ?

##参照

| 名前                                         | 説明 |
|----------------------------------------------|------------------|
| [`bucket_count`](./bucket_count.md)          | バケット数の取得 |
| [`max_bucket_count`](./max_bucket_count.md)  | 最大バケット数の取得 |
| [`bucket`](./bucket.md)                      | キーで指定したバケットのインデックス（添え字）を取得 |
| [`begin(size_type)`](./begin-size_type.md)   | インデックス（添え字）で指定したバケット内の先頭要素を指すイテレータを取得 |
| [`end(size_type)`](./end-size_type.md)       | インデックス（添え字）で指定したバケット内の最終要素の次を指すイテレータを取得 |
| [`cbegin(size_type)`](./cbegin-size_type.md) | インデックス（添え字）で指定したバケット内の先頭要素を指す読み取り専用イテレータを取得 |
| [`cend(size_type)`](./cend-size_type.md)     | インデックス（添え字）で指定したバケット内の最終要素の次を指す読み取り専用イテレータを取得 |

