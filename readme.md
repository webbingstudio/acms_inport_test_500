a-blog cms CSVインポートテスト
====================

これは、「a-sap:a-blog cms札幌勉強会」で使用した、CSVインポートハンズオン用のテストデータです。  
a-blog cmsバージョン2.5.0以上で動作を確認しています。

勉強会の素材、動作検証、他のCMSからのコンバートにご利用ください。

## 含まれる情報

以下のランダムなデータが100件または500件インポートされます。

- 投稿日時
- タイトル
- エントリーコード
  - test-(1からの連番)
- テキストユニット
  1. 中見出し: unit@h3
  1. 本文: unit@p
- カスタムフィールド
  1. シングルチェックボックス: field_test01
    - 0 or 1
  1. テキスト: field_test02
    - あいうえお, かきくけこ ... わをんっー
  1. マルチチェックボックス: field_test03
    - みかん, 林檎, ブドウ, banana

## テストデータのパーマリンクについて

パーマリンクを「test-(連番)」以外にしたい場合は、事前にentry_code列を削除してください。この場合は、a-blog cms管理ページの「コンフィグ＞編集設定」で指定したフォーマットに従い、a-blog cmsのシステム上の連番が付与されます。

## 利用方法

### 1. CSVインポートを行う

リポジトリ内の「acms_inport_test_500.csv」を管理ページからインポートしてください。  
CSV側でカテゴリー指定は行っていません。カテゴリー選択は任意で行ってください。

### 2. 一覧ページをカスタムフィールド検索に対応させる

Simple2016は、カスタムフィールド検索に対応していません。以下の手順で有効化してください。

1. 任意のカテゴリー一覧で、エントリーを表示している箇所にカーソルを置くと、右上に「モジュール」というリンクが表示されるのでクリックしてください。
1. モジュールID「summary_index」の設定画面となります。「条件設定」のタブ内、「引数」の項にある「フィールド」欄を探してください。
1. チェックボックスにチェックを入れて保存してください（リクエストしたURLにフィールド検索のキーがあれば参照するようになります）。

### 3. カスタムフィールドが反映されているかテストする

以下のURLを直接入力し、検索結果のエントリータイトルが「1番おき」となっていることを確認してください。

http://（インポートしたブログのURL）/field/field_test01/1/

### 4. カスタムフィールドの内容を表示する

現在反映しているテーマ内のentry.htmlの任意の場所に、「/asap08@simple2016/entry_field_test.txt」の内容をコピー・ペーストしてください。各エントリーのカスタムフィールドの内容を確認できます。

### 5. カスタムフィールドを編集可能にする

現在反映しているテーマの「/admin/entry/field.html」を、「/asap08@simple2016/admin/entry/field.html」の内容に置き換えてください。  
編集画面からフィールドを編集できるようになります。

## 補足

- フォーマットの詳細は公式ドキュメント「データ管理」を参照ください。<br>[データ管理 | ドキュメント | a-blog cms 制作者向け情報](http://developer.a-blogcms.jp/document/datamanagement/)
- Simple2016以外のテーマを使っている場合や、すでにカスタムフィールドを追加している場合は、既存のフィールドを上書きしないようご注意ください。
- ユニットのセル名を「unit@html」とするとHTML直接表示、「unit@markdown」とするとマークダウン記法となります。
- 異なるユニットを混在させたり、テキスト以外のユニットに対応することは現時点では難しいようです。
- 画像カスタムフィールドのインポートも可能なようですが、テストデータは現状、テキストのみとなっています。

以上
