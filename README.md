# calendar

```
   calendar --help
SYNOPSIS
    calendar [-A num] [-B num] [-f calendarfile]
For more detail, please see https://github.com/cympfh/calendar
```

Linux に入ってる CALENDAR(1) の使ってる機能だけを残して欲しい機能を追加したもの

## 残っているもの

- `-A num` 今日プラス num 日後まで出力
- `-B num` 今日マイナス num 日前から出力
- `-f calendarfile` calendarfile を読み込む

## 無いもの

- `-f` が指定されないとき、デフォルトでカレントディレクトリの `calendar` を読み込んでいましたが、消えました. どこで calendar コマンドを打つかは分からないからです. `cd` してから `calendar` するエイリアスまでわざわざ作っていました. 不毛です.
- その他のオプション: 色々あったけれど、使わないことに気付いたので実装しません

## 追加されたもの

- 年の概念: 今までは `MM/DD` と指定すれば毎年のその日だと解釈しました. 本来、calendar は毎年普遍の行事 (記念日や故人の命日など) を見て楽しむためのものだったからです. 本コマンドでは、年まで指定すれば、その年固有の行事として解釈します.

## calendar フォーマット

基本的にはオリジナルと変わりません.

1. 空行は無視する
1. `//` で始まる行は無視する
1. `#` で始まる行は `#include<file>` として正規表現マッチする
    - 相対パスだとして `file` を読み込む
1. 他の行は `\t` で区切って前半を日付として解釈する

### サンプル

`sample/calendar` を読んで見て下さい.
これを出力するには

```bash
./calendar -f sample/calendar
```

とすればよいです.

