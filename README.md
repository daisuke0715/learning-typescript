# 学習メモ

## 環境構築
- npm initコマンド
  - インストールしたパッケージ、依存関係などをpackage.jsonで管理することができる
  - これらを実行せずとも、エラーになることはないし、パッケージもインストールされるが、パッケージの管理のため作成しておいた方がいい
  - （参考資料）https://qiita.com/sugurutakahashi12345/items/1049a33b86225f6345f

- npx tsc --init
  - TypeScriptがインストールされたタイミングで、`npx tsc {filename} `でコンパイルが可能になるが、複数ファイルをコンパイルしたいときに、一気にコンパイルする事になってしまう
  - TypeScriptのプロジェクト作成
  - `npx tsc --init` => `tsconfig.json`を生成
  - 生成後、同一ディレクトリ配下のフォルダ+サブフォルダはTSによって管理されるようになる
  - tsconfig.jsonにはTSファイルがどのようにコンパイルされるかなどをコントロールする設定が記載されている
  - （参考資料）https://qiita.com/eiji-noguchi/items/8c1d3741ac9f2857b230

- npx tsc  
  - コンパイル時のコマンド
  - tsconfigの `outDir`でコンパイル後のファイルの出力先をできる  

<br>
<br>
<br>

## TypeScriptインプット項目
- getter、setterについて
  - 疎結合の概念からクラス内のプロパティは外部から直接参照できないようにする  
  - そのためクラス内部のプロパティ、メソッドにアクセス修飾子privateをつけることで同一クラス内でしか参照できないようにするのが一般的
  - 外部から参照する際に使われるのが、getter、setterメソッドを使って参照すること
<br>

- 複数の型があり得る場合の指定方法
  「 | 」で型を区切って定義する  
  Ex. string | undefined

