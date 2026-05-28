# Laravel Lesson レビュー①

## Todo一覧機能

### Todoモデルのallメソッドで実行しているSQLは何か
- select * from todos;
### Todoモデルのallメソッドの返り値は何か
- DBデータの入っているCollectionオブジェクト
### 配列の代わりにCollectionクラスを使用するメリットは
- クラスに設定されている多くのメソッドをそのまま使用できるメリットがある。
### view関数の第1・第2引数の指定と何をしているか
- 第一引数は、bladeファイル。第二引数は連想配列
### index.blade.phpの$todos・$todoに代入されているものは何か
- $todosに代入されているものは、Collectionクラス。
- $todoに代入されているのはTodoクラスのインスタンス。
## Todo作成機能

### Requestクラスのallメソッドは何をしているか
- ユーザが送信したデータを連想配列の形にして受け取っている
### fillメソッドは何をしているか
- 連想配列のキーとカラムを自動的に一致させて、$todoに代入している。
### $fillableは何のために設定しているか
- 今回content以外のデータのDBの入力を禁止しているので、他人のuser_idになりすまして、dbに保存することを防ぐことができる。
### saveメソッドで実行しているSQLは何か
- INSERT INTO todos (content, created_at, updated_at) 
-  VALUES
-  ('テスト文章', '作成日時', '作成日時');
### redirect()->route()は何をしているか
- 保存した後に、indexへ強制的に戻している。
## その他

### テーブル構成をマイグレーションファイルで管理するメリット
- SQLのコマンドを覚えなくてもdbを操作することができる。DBの状態を他人と共有できる。
### マイグレーションファイルのup()、down()は何のコマンドを実行した時に呼び出されるのか
- upメソッドは、`php artisan migrate`を実行した際に呼び出される。
- downメソッドは`php artisan migrate:rollback`を実行した際に呼び出される。
### Seederクラスの役割は何か
- コード上で、テストデータの一括入力ができる。dbの情報（レコード）の状態を他の作業者と合わせること。
### route関数の引数・返り値・使用するメリット
- 引数は飛ばしたいページを指定する。
- 返り値は`http://localhost/todo`
- メリットは可読性が高いことと、修正時にweb.phpの該当部分で保守性が高い。
### @extends・@section・@yieldの関係性とbladeを分割するメリット
- 共通している部分を共通化することで、保守性が上がる。
- @extendsは継承する親bladeの指定。子bladeの@section〜@endsectionで囲われた部分を当てはめる。@yieldは親bladeの当てはめる空間部分。
### @csrfは何のための記述か
- クロスサイトリクエストフォージェリに対応するための記述
- tokenを生成してpost方式で送信する。
### {{ }}とは何の省略系か
- `<?php echo　htmlspecialchars($todo->content, ENT_QUOTES, 'UTF-8');?>`
- echoで呼び出すのと同時に、XSS対策用のエスケープ処理をしている。