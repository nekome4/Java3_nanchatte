# Java3_nanchatte
なんちゃって、開発プロジェクト

GitHubでは、リードミーを、wiki形式で作成することができます。
開発メンバーに共有する情報を書きましょう。


## Java初心者？のための、よく使うJavacコマンドの書きかた
srcフォルダ、buildフォルダ作成ずみとします。

ここを読め! [javac - Java プログラミング言語コンパイラ](https://docs.oracle.com/javase/jp/6/technotes/tools/windows/javac.html)

* オプション無し(カレントディレクトリにソースファイルがある場合や、カレントディレクトリからのパス指定する場合）

  ```
  > javac ソースファイル名
  
  （例）
  > javac Test.java
  > javac src/Test.java
  
  ```
* ソースパス指定（カレントディレクトリ以外に、読み込みたいソースコードがある場合）
  ```
  > javac -sourcepath パス ソースファイル名
  
  (例)
  > javac -sourcepath src *.java         カレントディレクトリとsrcディレクトリにある〜.javaを一括コンパイル
  
  ```
* エンコード指定（特定の文字コードで書かれたソースファイルをコンパイルする）
  ```
  > javac -encoding コード記号 ソースファイル名
  
  （例）
  > javac -encoding UTF8 src/Test.java   UTF8で書かれたTest.javaを文字化けせずにコンパイルする
  > javac -encoding SJIS src/Test.java
  ```
* クラスファイルの保存先指定
  ```
  > javac -d 保存先パス ソースファイル名
  
  (例)
   > javac -d build src/Test.java        コンパイルした結果（package/Test.class）は、buildフォルダ以降に格納される
 
 ```
* クラスファイル、Jarファイルの読み込み先指定
  ```
  > javac -cp 読み込み先パス
  
  （例）buildフォルダにある、Hoge.classをインポートするソースファイルをコンパイルする
   > javac -cp build src/Test.java
   
   (例) インポートするクラスファイルが、複数のフォルダ(build,hoge)に分散している場合
   > javac -cp build;hoge src/Test.java (windowsコマンドプロンプトの場合)
   > javac -cp build:hoge src/Test.java (ソースツリーのターミナルの場合）
  
  ```
* 複合パターン
  ```
  
   (例) srcフォルダにあるTest.javaが、すでにコンパイル済みの、buildフォルダにある、Hoge.classをインポートしていて、Test.javaコンパイル後は、buildフォルダに収めたい。なお、Test.javaはUTF8で記述されている
  
   > javac -encoding UTF8 -d build -cp build src/Test.java
   ```

## 初心者？のための、よく使うJava実行コマンド
ここを読め！ [java - Java アプリケーション起動コマンド](https://docs.oracle.com/javase/jp/1.3/tooldocs/linux/java.html)

* 普通の実行
   ``` 
   > java パッケージ.実行クラス名
   
   (例) カレントディレクトリにある、Test.classを実行する(パッケージなし）
   > java Test
   
   ```
* 読み込み元指定
  ```
   > java -cp 読み込み元フォルダ パッケージ.実行クラス名
   
   (例) build フォルダ以降にある、Test.class(パッケージ hoge)を実行
   > java -cp build hoge.Test
   
   ```
* コマンドライン引数あり
  ```
  > java クラス名 引数 引数 ・・・
  
  (例) 実行時に、コマンドライン引数 "hoge" "foo" を渡す
  > java -cp build Test hoge foo
  
  ```
  
