# ファイルパスからファイル名を取得する方法

UiPathで「ファイル選択(SelectFile)」を使用してファイルパスを取得し、ファイルパスからファイル名だけを抽出する方法

## 変数の作成

| 変数名 | 変数の型 | 備考 |
| ----- | ------- | ---- |
| FilePath | String |
| FileName | String |
| FilePathArray| String[]| Array of String |

上記の表の通りに変数を作成してください。

![image.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/556204/dc99410b-3e81-0413-4a7a-707f574163ab.png)

## ファイルパスを取得する

まず「ファイルを選択」を配置します。
アクティビティ検索欄に「ファイルを選択」と入力するか
`システム` -> `ダイアログ` -> `ファイルを選択`から配置してください。

配置が完了したら、右側のプロパティ欄の「出力」に`FilePath`を入力します。

![image.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/556204/8eb00821-f585-59e7-363d-3a5a704e3bc5.png)


## ファイルパスからファイル名を取得する

次に「代入」を配置します。
デフォルト設定でお気に入りにあるのでそこから配置してください。

配置が完了したら、`FilePathArray = FilePath.Split("\"c)`となるように入力します。

![image.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/556204/a27205f8-1171-9a44-8471-399fcdb5766f.png)

その下に「代入」をもう1つ配置してください。

配置が完了したら、`FileName = FilePathArray(FilePathArray.Length - 1)`となるように入力します。

![image.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/556204/55295059-e8a1-edd4-c526-fbff2c6dc6e6.png)

### 補足

例）デスクトップにある「test.txt」を選択した場合

| 変数名 | 設定値 | 
| ------ | ----- |
|FilePath| C:\Users\Desktop\test.txt |

`FilePathArray = FilePath.Split("\"c)`で`FilePathArray`は以下の表のようになっています。

| インデックス | 0 | 1 | 2 | 3 |
| ----------- |:-:|:-:|:-:|:-:|
| 配列内の値  | C: | Users | Desktop | test.txt |

一番最後を指定することで、ファイル名を取得できます。
`FilePathArray.Length`では要素数を取得するため、上記の表の通り4つ要素があるため**FilePathArray.Length=4**となります。
`FilePathArray.Length - 1`とすることで最後のファイル名部分を指定することができます。

 


