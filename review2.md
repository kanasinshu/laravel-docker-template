# Laravel Lesson レビュー②

## Todo編集機能

### @method('PUT')を記述した行に何が出力されているか
- `<input type ="hidden" name="_method" value = "PUT"> `
### findメソッドの引数に指定しているIDは何のIDか
- 編集をしたいcontentのid。クエリパラメータとしてURLに加えられているものを引数としている。
### findメソッドで実行しているSQLは何か
- `SELECT * from todos where id = （編集するid）`
### findメソッドで取得できる値は何か
- Todoインスタンスの中に指定したidのレコードのデータが格納されている。
### saveメソッドは何を基準にINSERTとUPDATEを切り替えているのか
- すでに保存されている情報か新規の入力か確認して切り替えている。
## Todo論理削除

### traitとclassの違いとは
- classは１つしか継承できないですが、traitは複数のメソッドなどを使うことができます。traitはclassと違いインスタンス化はできません。
### traitを使用するメリットとは
- コードが短くなること。classと違い使いたい機能があれば、付け加えることができる。また変更の際はtraitの定義を変更することでtraitを使用しているクラスの修正が可能となる。
## その他

### TodoControllerクラスのコンストラクタはどのタイミングで実行されるか
- Route関数からTodoController内のインスタンス化した時
### RequestクラスからFormRequestクラスに変更した理由
- バリデーション専用のクラスを分けることで、可読性を向上するため。
### $errorsのhasメソッドの引数・返り値は何か
引数はチェックしたい入力欄のname属性で今回はcontentです。返り値は真偽値です。
### $errorsのfirstメソッドの引数・返り値は何か
引数はチェックしたい入力欄のname属性で今回はcontentです。返り値は文字列です。
### フレームワークとは何か
- 枠組みのことで、すでに処理が書かれているプログラムがまとまっているツール。効率的にプロダクトを生み出すことができる。
### MVCはどういったアーキテクチャか
- WEBサーバから受け取ったリクエストを受け取ってからWEBサーバに返却するまでをModel,View,Controllerに分けて、役割を持たせるアーキテクチャ
### ORMとは何か、またLaravelが使用しているORMは何か
- ORM(Object-Relational Mapping)の一つであるEloquent。
- ORMとは、SQLを直接操作することなくやり取りすることができます。
### composer.json, composer.lockとは何か
- composer.jsonは、プロジェクトに必要な外部ライブラリやバージョンがJSON形式で記述されています。
- composer.lockはcomposer.jsonでインストールした詳細なバージョンが記載されています。チーム内で環境を生まないために使用される。
### composerでインストールしたパッケージ（ライブラリ）はどのディレクトリに格納されるのか
vendor内に全て保存される。