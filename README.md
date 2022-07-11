# vue_cli_app
【課題】Vue CLI メモアプリSPA版

### 一覧、詳細
メモの1行目をタイトルとして一覧表示する。タイトルをクリックするとそのメモの編集状態に移行する。
編集状態＝詳細

[![Image from Gyazo](https://i.gyazo.com/2fe5afa091a5615762dc851cfced3a6c.gif)](https://gyazo.com/2fe5afa091a5615762dc851cfced3a6c)

### 追加
＋をクリックすると「新規メモ」というメモファイルが作成され、編集状態に移行する。

[![Image from Gyazo](https://i.gyazo.com/4db54fce8a0a634171541e4669cabd68.gif)](https://gyazo.com/4db54fce8a0a634171541e4669cabd68)

### 編集
テキストエリアにメモの内容を表示し、編集できる。編集ボタンをクリックすると保存される。

[![Image from Gyazo](https://i.gyazo.com/3682836d85610cacf76a330bbc8ac488.gif)](https://gyazo.com/3682836d85610cacf76a330bbc8ac488)

### 削除
編集状態で削除ボタンをクリックするとメモは削除される。そのあとは一覧の状態に移行する。

[![Image from Gyazo](https://i.gyazo.com/a6b074f85ef75e5e08bdeb6bbe3d9d96.gif)](https://gyazo.com/a6b074f85ef75e5e08bdeb6bbe3d9d96)

### 保存先
LocalStorageを選択