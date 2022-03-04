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

- 辞書型の定義について (Dictionary)
  <br>
  ```
  連想配列の宣言

  // keyがstring型の連想配列
  var hash1: { [key: string]: string; } = {};

  // 値を格納
  hash1['a'] = 'a'; 


  // keyがnumber型の連想配列
  var hash2: { [key: number]: string; } = {};

  // 値を格納
  hash2[1] = 'b'; 


  // 型未指定の連想配列
  var hash3: { [key]: string; } = {};

  // 値を格納(string/numberどっちもいける)
  hash3['a'] = 'c'; 
  hash3[1] = 'd';
  ```
  [参考資料：TypeScriptの型と基本的な書き方#連想配列の宣言](https://qiita.com/Rock22/items/d7ae96464bdbf297c6ec#%E9%80%A3%E6%83%B3%E9%85%8D%E5%88%97%E3%81%AE%E5%AE%A3%E8%A8%80)
  [参考資料：TypeScriptの型: 辞書型を定義する (Dictionary)](https://maku.blog/p/x3ocp9a/)