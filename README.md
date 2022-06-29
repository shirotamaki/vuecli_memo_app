# vue_cli_app
【課題】Vue CLI メモアプリSPA版

### 一覧、詳細
メモの1行目をタイトルとして一覧表示する。タイトルをクリックするとそのメモの編集状態に移行する。
編集状態＝詳細

[![Image from Gyazo](https://i.gyazo.com/55a2a24b6f8c942b9a74db7636f2a814.gif)](https://gyazo.com/55a2a24b6f8c942b9a74db7636f2a814)

### 追加
＋をクリックすると「新規メモ」というメモファイルが作成され、編集状態に移行する。

[![Image from Gyazo](https://i.gyazo.com/53666bf3492109dd0197915572230e6c.gif)](https://gyazo.com/53666bf3492109dd0197915572230e6c)

### 編集
テキストエリアにメモの内容を表示し、編集できる。編集ボタンをクリックすると保存される。

[![Image from Gyazo](https://i.gyazo.com/d50ff2ea475a91ca93971512fde42b98.gif)](https://gyazo.com/d50ff2ea475a91ca93971512fde42b98)

### 削除
編集状態で削除ボタンをクリックするとメモは削除される。そのあとは一覧の状態に移行する。

[![Image from Gyazo](https://i.gyazo.com/672271f301c0bf86eafbcf03e1ef675e.gif)](https://gyazo.com/672271f301c0bf86eafbcf03e1ef675e)

### 保存先
LocalStorageを選択