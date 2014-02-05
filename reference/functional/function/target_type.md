#target_type(C++11)
```cpp
const std::type_info& target_type() const noexcept;
```
* type_info[link /reference/typeinfo/type_info.md]

##概要
元となる関数の型情報を取得する。


##戻り値
呼び出す関数を持っていれば、その関数の型を表す[`type_info`](/reference/typeinfo/type_info.md)オブジェクトを返す。呼び出す関数を持っていなければ、`typeid(void)`を返す。


##例
```cpp
#include <iostream>
#include <functional>

struct ident {
  int operator()(int x) const
  { return x; }
};

int main()
{
  std::function<int(int)> f = ident();

  if (f.target_type() == typeid(ident)) {
    std::cout << "f has ident" << std::endl;
  }
  else {
    std::cout << "f doesn't have ident" << std::endl;
  }
}
```

###出力
```
f has ident
```


##バージョン
###言語
- C++11


###処理系
- [Clang, C++11 mode](/implementation#clang.md): 3.0
- [GCC, C++11 mode](/implementation#gcc.md): 4.3.6
- [Visual C++](/implementation#visual_cpp.md): ??


##参照
