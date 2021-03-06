#new
* new[meta header]

`<new>`ヘッダは、プログラムが動的に記憶域を確保し、管理するための機能を定義し、記憶域の管理のエラー報告（例外の送出）についても定義する。このヘッダはグローバルネームスペースの`new`演算子および`delete`演算子をオーバーロードする。replacement-new を行いたい場合などに用いる。


##型

| 名前 | 説明 | 対応バージョン |
|-----------------------------------|-------------------------------------------------|-------|
| [`bad_alloc`](./new/bad_alloc.md) | 何らかの理由で記憶域の動的確保に失敗するなど、`get_new_handler()`が`nullptr`を返した場合にスローされる例外(class) | |
| [`bad_array_new_length`](./new/bad_array_new_length.md) | 動的に記憶域を確保しようとする配列の長さが0未満または処理系の最大値以上の場合にスローされる例外(class) | C++11 |
| [`nothrow_t`](./new/nothrow_t.md) | 例外をスローしないための`std::nothrow`の型 | |
| [`new_handler`](./new/new_handler.md) | `new`失敗時に呼ばれる関数の型 | |


##関数

| 名前                                          | 説明                                           | 対応バージョン |
|-----------------------------------------------|------------------------------------------------|----------------|
| [`get_new_handler`](./new/get_new_handler.md) | `new`失敗時に呼ばれる関数を取得する(function)  | C++11          |
| [`set_new_handler`](./new/set_new_handler.md) | `new`失敗時に呼ばれる関数を設定する(function)  |                |
| [`operator new`](./new/op_new.md)             | 動的に記憶域を確保する(function)               |                |
| [`operator new[]`](./new/op_new[].md)         | 動的に配列の記憶域を確保する(function)         |                |
| [`operator delete`](./new/op_delete.md)       | 動的に確保した記憶域を解放する(function)       |                |
| [`operator delete[]`](./new/op_delete[].md)   | 動的に確保した配列の記憶域を解放する(function) |                |
