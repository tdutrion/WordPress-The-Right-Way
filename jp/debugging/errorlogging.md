# エラーの記録

エラーの記録にはいくつか種類がありますが、主なものは以下になります:

 - 表側にエラーを表示する
 - ログファイルにエラーを書き込む
 - 何も表示させない

本番環境ではエラーはログファイルに書き込んだほうがいいでしょう。

## 警告(Warning) vs エラー(Error)

PHPがどのように設定されているかにもよりますが、警告(Warning)が表示されることもあります。警告(Warning)はPHPを止めてしまうわけではありませんが、問題となり得ることを示します。例えば:

```php
$my_array = array(
    'alice' => 5,
    'bob' => 6
);
echo $my_array['eve'];
```

ここでは`$my_array`内の'eve'エントリーをエコーしようとしているのですが、そのようなエントリーはありません。PHPは空の値を作り警告を記録します。警告(Warning)はバグやミスを指し示すのです。

## PHPエラーレポーティング

`php.ini`に何が定義されていのかによりますが、PHPにはエラーレポーティングレベルというものがあります。そのレベル以下のものはすべて無視されるか単なる警告とみなされます。これはサーバーによって様々です。

## `@` エラー制御演算子

エラー制御演算子 `@` は決して使ってはいけません。これはコードのエラーと警告を隠しますが、普通の人が望むような動作はしません。

`@` はコマンド上のエラー報告レベル設定によって動作するので、エラーが記録されません。これは、普通の人が望むような、エラーの発生を防止するものではありません。これは致命的なエラーが捉えられないか、記録されないようにすることを意味します。エラー制御演算子 `@` の使用は避け、このインスタンスはすべて疑いをもって扱うようにします。