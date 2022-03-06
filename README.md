# 学習メモ

## 環境構築
- npm initコマンド
  - インストールしたパッケージ、依存関係などをpackage.jsonで管理することができる
  - これらを実行せずとも、エラーになることはないし、パッケージもインストールされるが、パッケージの管理のため作成しておいた方がいい
  - （参考資料）https://qiita.com/sugurutakahashi12345/items/1049a33b86225f6345f
<br>
- npx tsc --init
  - TypeScriptがインストールされたタイミングで、`npx tsc {filename} `でコンパイルが可能になるが、複数ファイルをコンパイルしたいときに、一気にコンパイルする事になってしまう
  - TypeScriptのプロジェクト作成
  - `npx tsc --init` => `tsconfig.json`を生成
  - 生成後、同一ディレクトリ配下のフォルダ+サブフォルダはTSによって管理されるようになる
  - tsconfig.jsonにはTSファイルがどのようにコンパイルされるかなどをコントロールする設定が記載されている
  - （参考資料）https://qiita.com/eiji-noguchi/items/8c1d3741ac9f2857b230
<br>
- tsc  
  - コンパイル時のコマンド
  - tsconfigの `outDir`でコンパイル後のファイルの出力先をできる  
<br>
- node [ コンパイル後のjsファイル ]
  - jsファイルの実行コマンド

<br>
<br>
<br>

## TypeScript
- getter、setterについて
  - 疎結合の概念からクラス内のプロパティは外部から直接参照できないようにする  
  - そのためクラス内部のプロパティ、メソッドにアクセス修飾子privateをつけることで同一クラス内でしか参照できないようにするのが一般的
  - 外部から参照する際に使われるのが、getter、setterメソッドを使って参照すること
  [参考資料：typescriptにおけるgetterとsetterを理解する](https://qiita.com/kuropp/items/ebefeec110ea6a2beb62)
<br>

- 複数の型があり得る場合の指定方法
  「 | 」で型を区切って定義する  
  Ex. string | undefined
  [参考資料:Typescriptの型初級](https://qiita.com/uhyo/items/da21e2b3c10c8a03952f)
<br>

- Object型の取り扱いについて
  TypeScriptではobject型の指定をした場合、そのオブジェクトがどの様なプロパティを持っているかを認識できず、アクセスすることができないので、特別な理由がない限りはobject型を指定しない
  [参考資料：【TypeScript】Object型について](https://marsquai.com/a70497b9-805e-40a9-855d-1826345ca65f/1dc3824a-2ab9-471f-ad58-6226a37245ce/9a50771d-825f-4186-a56e-ba5f0d07b0e8/#h3-610a8202-f03c-4a07-8aa5-9a49e04cd316-0f4029b7-b51e-44a7-8832-8d590f35d917)

<br>

- 連想配列について（ => ハッシュと同義）
  連想配列とは、自動的に割り当てられる数字をキーとして持つかわりに、自由に任意の文字列を割り振ることができる配列です。キーを任意に指定できることによって、そこに格納されている値が何のことであるかということがより簡単に連想できるようになっている
  [参考資料：JavaScriptの基本である連想配列をマスターする](https://techplay.jp/column/528)


<br>

- ジェネリクスの型定義について
  - 概要
    - Genericsは抽象的な型引数を使用して、実際に利用されるまで型が確定しないクラス・関数・インターフェイスを実現する為に使用されます。
  - メリット：
    - 下記のように同じようなコードを別の型で繰り返す場合、別関数で定義して処理を冗長化することを防止してくれる
    - クラスであればインスタンス化するまで、関数であれば実行された際に初めてインスタンス化された値型で確定するので、受け入れるコンストラクタ引数、引数に対して、強い制約（1つ1つの処理単位での型の制約）を付け加えることができ、不適切な値が使用された際に、コンパイルエラーをできる吐かせる事ができる
[参考資料：ジェネリクスのメリットって、何？](https://zenn.dev/dowanna6/articles/63fdebe8dd167f)
[参考資料：TypeScriptの型入門 ジェネリクスについて](https://qiita.com/uhyo/items/e2fdef2d3236b9bfe74a#%E3%82%B8%E3%82%A7%E3%83%8D%E3%83%AA%E3%82%AF%E3%82%B9)
[参考資料：TypeScriptジェネリクス](https://qiita.com/tfrcm/items/cd8dafcc8ee4f824ccf5)

<br>

- クラスのオブジェクトを外部からメソッドを使って参照する際に別変数のコピーを使用して返り値を設定する理由
  - アンダースコア "_" で始まるプロパティは内部のもので、外部のオブジェクトから触るべきではない
  - これは、外部からアクセスすることで意図しないタイミングでの変数のデータの更新により、意図しない挙動になってしまう可能性をなくすため
  - 例えば、名前のデータがクラスにあるとして、そのデータは、_name プロパティに格納され、アクセスは getter/setter と通して行われる。
  - 技術的には、外部コードは `user._name`を使うことによって、 外部から`_name`にアクセスできるが、アンダースコア "_" で始まるプロパティは内部のもので、外部のオブジェクトから触るべきではないのは慣例

<br>

- objectのkeyのデータを取得する方法
  - keyof演算子で取得できる  
    [参考資料：keyofを使ってオブジェクトと適切なキーを取る関数作成](https://negalog.com/typescript-keyof-generics/)


<br>

- オブジェクトのコピーについて
  - Object.assign() を使う方法ですね。元々この関数は、一番最初に渡されたオブジェクトに、その後ろに渡されたオブジェクトを結合していく関数です。
  - ポイントは、今回は新しく作った空オブジェクト {} にtest を結合しているので、できあがる内容は test と同じものだけど、オブジェクト自体は別物となる点
  - 同じ値を参照しないようにするためにコピーを別オブジェクトで作成している
<br>
<br>


  ```
  # 以下のコードだとダメ（これだと代入で同じものを参照しているから）
  var test = { a: 10 };
  var test_copy = test;
 
  test_copy.a = 20;
 
  console.log(test);


  // 実行結果
  [object Object] {
    a: 20
  } 

  # コピーを取る方法
  var test = { a: 10 };
  var test_copy = Object.assign({}, test);

  ```
  [参考資料：[JavaScript]オブジェクトのコピーの取り方](https://www.agent-grow.com/self20percent/2019/09/16/javascript-object-and-array-copy-es6/)
