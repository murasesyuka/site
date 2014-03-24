#align(C++11)
```cpp
namespace std {
  void* align(std::size_t alignment, std::size_t size,
              void*& ptr, std::size_t& space);
}
```

##概要
アラインメント調整された領域を得る。


##効果
範囲`[ptr, ptr + space)`の中にalignment`バイトでアラインメント調整された領域の`size`バイトに一致するバッファがあるなら、

- `ptr`を一致する領域の先頭アドレスへと更新し、
- `space`から使用したバイト数を減算する。

そのようなバッファがなければ、この関数は何もしない。


##戻り値
更新された`ptr`を返す。一致する領域がなければ、ヌルポインタを返す。


##例
```cpp
#include <iostream>
#include <memory>

int main()
{
  char buffer[256];
  void* ptr = buffer;
  std::size_t space = sizeof(buffer) - 1;

  // intアラインメントで、intをN個確保。
  std::size_t N = 3;
  if (std::align(alignof(int), sizeof(int) * N, ptr, space)) {
	std::cout << ptr << " " << space << std::endl;
  }
}
```

###出力例
```
0x7fffd930ca40 255
```

##バージョン
###言語
- C++11

###処理系
- [Clang, C++11 mode](/implementation#clang.md): 3.0
- [GCC, C++11 mode](/implementation#gcc.md): (4.8.2時点で未実装)
- [ICC](/implementation#icc.md): ??
- [Visual C++](/implementation#visual_cpp.md) ??


##参照
