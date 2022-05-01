# Handontableを使うためのメモ

Handsontableのバージョンは、商用フリーの最終バージョンである6.2.2を使用する。

## 不具合の修正

※本修正は、最新版でも対応されていないため予期せぬ問題が出る可能性があります。

使用される際には、確認のうえ自己責任で適用してください。

### Undo Redo

minSpareRowsを指定して、新しい行を追加できるようにしておくと
行追加後にUndoを行うと、UndoRedoバッファがクリアされて正しく処理されなくなる。

### 新規行に全項目(null又は空白)の行を追加すると新しい行が追加されない

行を追加してもcountRows関数が、nullおよび空白のみの行をminSpareRowsの行として判定している。
ENTERキーの処理部分のみの問題のようなので、その部分だけをスキップさせる。

## 列に隠し項目を持たせる

設定するデータの列数をヘッダに使用する列＋N(項目で必要な分だけ)で作成する。

````` javascript
columns: ["1","2"]
data: [
	["data1", "data2", "隠し項目"]
]
`````