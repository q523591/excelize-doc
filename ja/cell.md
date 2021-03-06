# セル

## セル値設定 {#SetCellValue}

```go
func (f *File) SetCellValue(sheet, axis string, value interface{})
```

指定されたワークシート名とセル座標に基づいて、セルの値を設定します。

|支持的数据类型|
|---|
|int|
|int8|
|int16|
|int32|
|int64|
|uint|
|uint8|
|uint16|
|uint32|
|uint64|
|float32|
|float64|
|string|
|[]byte|
|time.Duration|
|time.Time|
|bool|
|nil|

## ブール値設定 {#SetCellBool}

```go
func (f *File) SetCellBool(sheet, axis string, value bool)
```

指定されたワークシート名とセル座標に基づいて、ブール型 (Boolean) のセルの値を設定します。

## 既定の文字の種類の値を設定する {#SetCellDefault}

```go
func (f *File) SetCellDefault(sheet, axis, value string)
```

指定されたワークシート名とセル座標に基づいて、文字セルの値を設定し、特殊文字に対してはフィルタされません。

## 実数を設定する {#SetCellInt}

```go
func (f *File) SetCellInt(sheet, axis string, value int)
```

指定されたワークシート名とセル座標に基づいて、実際のセルの値を設定します。

## 文字列値の設定 {#SetCellStr}

```go
func (f *File) SetCellStr(sheet, axis, value string)
```

指定したワークシート名とセル座標に基づいて文字セルの値を設定すると、文字は特殊文字でフィルタリングされ、文字列の累積長は `32767` を超えてはならず、余分な文字は無視されます。

## セルスタイルの設定 {#SetCellStyle}

```go
func (f *File) SetCellStyle(sheet, hcell, vcell string, styleID int)
```

指定されたワークシート名、セル座標領域、およびスタイルインデックスに基づいて、セルの値を設定します。スタイルインデックスは `NewStyle` 関数を使用して取得できます。同じ座標領域内の `diagonaldown` と `diagonalup` は同じ色で保持する必要があることに注意してください。

- 例1、ワークシート `D7` セル `Sheet1` の境界線のスタイルを設定します:

```go
style, err := xlsx.NewStyle(`{"border":[{"type":"left","color":"0000FF","style":3},{"type":"top","color":"00FF00","style":4},{"type":"bottom","color":"FFFF00","style":5},{"type":"right","color":"FF0000","style":6},{"type":"diagonalDown","color":"A020F0","style":7},{"type":"diagonalUp","color":"A020F0","style":8}]}`)
if err != nil {
    fmt.Println(err)
}
xlsx.SetCellStyle("Sheet1", "D7", "D7", style)
```

<p align="center"><img width="612" src="./images/SetCellStyle_01.png" alt="Excel セルの枠線のスタイルを設定する"></p>

セル `D7` の4つの境界は、`NewStyle` 関数を呼び出すときにパラメータに関連する異なるスタイルと色に設定されており、その章のドキュメントを参照するために異なるスタイルを設定する必要があります。

- 例2では、ワークシート `D7` セル `Sheet1` という名前のグラデーションスタイルを設定します:

```go
style, err := xlsx.NewStyle(`{"fill":{"type":"gradient","color":["#FFFFFF","#E0EBF5"],"shading":1}}`)
if err != nil {
    fmt.Println(err)
}
xlsx.SetCellStyle("Sheet1", "D7", "D7", style)
```

<p align="center"><img width="612" src="./images/SetCellStyle_02.png" alt="セルのグラデーションスタイルを設定する"></p>

セル `D7` はグラデーション効果の塗りつぶしに設定され、グラデーションの塗りつぶし効果は `NewStyle` 関数を呼び出すときのパラメーターに関連しており、その章のドキュメントを参照するために異なるスタイルを設定する必要があります。

- 例3では、ワークシート `D7` セル `Sheet1` という名前の単色の塗りつぶしを設定します:

```go
style, err := xlsx.NewStyle(`{"fill":{"type":"pattern","color":["#E0EBF5"],"pattern":1}}`)
if err != nil {
    fmt.Println(err)
}
xlsx.SetCellStyle("Sheet1", "D7", "D7", style)
```

<p align="center"><img width="612" src="./images/SetCellStyle_03.png" alt="セルに単色の塗りつぶしを設定する"></p>

セル `D7` は単色の塗りつぶしに設定されています。

- 例4では、ワークシート `D7` セルの文字間隔と回転角度を `Sheet1` という名前で設定します:

```go
xlsx.SetCellValue("Sheet1", "D7", "Style")
style, err := xlsx.NewStyle(`{"alignment":{"horizontal":"center","ident":1,"justify_last_line":true,"reading_order":0,"relative_indent":1,"shrink_to_fit":true,"text_rotation":45,"vertical":"","wrap_text":true}}`)
if err != nil {
    fmt.Println(err)
}
xlsx.SetCellStyle("Sheet1", "D7", "D7", style)
```

<p align="center"><img width="612" src="./images/SetCellStyle_04.png" alt="文字間隔と回転角度を設定する"></p>

- 例5の日付と時刻は、Excel が実数で表され、たとえば `2017/7/4  12:00:00 PM` が番号 `42920.5` で表すことができる。`Sheet1` という名前のワークシート `D7` セルの時刻形式を設定します:

```go
xlsx.SetCellValue("Sheet1", "D7", 42920.5)
xlsx.SetColWidth("Sheet1", "D", "D", 13)
style, err := xlsx.NewStyle(`{"number_format": 22}`)
if err != nil {
    fmt.Println(err)
}
xlsx.SetCellStyle("Sheet1", "D7", "D7", style)
```

<p align="center"><img width="612" src="./images/SetCellStyle_05.png" alt="セルの時間形式を設定する"></p>

セル `D7` は時刻形式で設定されています。 時刻形式のセルの幅が狭すぎて完全に表示できない場合は、`####` と表示され、調整列の幅をドラッグアンドドロップするか、適切なサイズに設定するために `SetColWidth` 関数を呼び出すことによって、列の大きさが適切であることを確認します。

- 例6、ワークシート `D7` という名前のセルのフォント、フォントサイズ、色、および傾きのスタイルを設定します：

```go
xlsx.SetCellValue("Sheet1", "D7", "Excel")
style, err := xlsx.NewStyle(`{"font":{"bold":true,"italic":true,"family":"Berlin Sans FB Demi","size":36,"color":"#777777"}}`)
if err != nil {
    fmt.Println(err)
}
xlsx.SetCellStyle("Sheet1", "D7", "D7", style)
```

<p align="center"><img width="612" src="./images/SetCellStyle_06.png" alt="セルのフォント、フォントサイズ、色、および傾きのスタイルを設定する"></p>

- 例7、ワークシート `D7` セル `Sheet1` という名前をロックして非表示にします:

```go
style, err := xlsx.NewStyle(`{"protection":{"hidden":true, "locked":true}}`)
if err != nil {
    fmt.Println(err)
}
xlsx.SetCellStyle("Sheet1", "D7", "D7", style)
```

セルをロックしたり数式を非表示にしたりするには、ワークシートを保護します。「校閲」タブで、「ワークシートの保護」をクリックします。

## ハイパーリンクの設定 {#SetCellHyperLink}

```go
func (f *File) SetCellHyperLink(sheet, axis, link, linkType string)
```

指定したワークシート、セル座標、リンクされたリソース、およびリソースの種類に基づいて、セルのハイパーリンクを設定します。 リソースの種類は、外部リンクアドレス `External` とブック内部の場所のリンク `Location` 2 種類に分割されます。

- 例1、ワークシート `A3` セル `Sheet1` という名前の外部リンクを追加します:

```go
xlsx.SetCellHyperLink("Sheet1", "A3", "https://github.com/360EntSecGroup-Skylar/excelize", "External")
// セルのフォントとアンダースコアのスタイルを設定する
style, _ := xlsx.NewStyle(`{"font":{"color":"#1265BE","underline":"single"}}`)
xlsx.SetCellStyle("Sheet1", "A3", "A3", style)
```

- 例2では、ワークシート `A3` セル `Sheet1` という名前の内部の場所のリンクを追加します:

```go
xlsx.SetCellHyperLink("Sheet1", "A3", "Sheet1!A40", "Location")
```

## セル値取得 {#GetCellValue}

```go
func (f *File) GetCellValue(sheet, axis string) string
```

指定されたワークシートとセルの座標に基づいてセルの値を取得し、戻り値を `string` 型に変換します。 セルの書式をセルの値に適用できる場合は、アプリの後の値が返され、それ以外の場合は元の値が返されます。

## 全セル値取得 {#GetRows}

```go
func (f *File) GetRows(sheet string) [][]string
```

ワークシート上のすべてのセルの値を、指定されたワークシート名 (大文字小文字の区別) に基づいて取得し、2次元配列として返し、セルの値を `string` 型に変換します。 セルの書式設定をセルの値に適用できる場合は、アプリの後の値が使用され、それ以外の場合は元の値が使用されます。

たとえば、ワークシート上のすべてのセルの値を取得および走査するには、`Sheet1` という名前の出力を使用します。

```go
for _, row := range xlsx.GetRows("Sheet1") {
    for _, colCell := range row {
        fmt.Print(colCell, "\t")
    }
    fmt.Println()
}
```

## ハイパーリンクを取得 {#GetCellHyperLink}

```go
func (f *File) GetCellHyperLink(sheet, axis string) (bool, string)
```

指定されたワークシート名 (大文字小文字を区別する) とセル座標に基づいてセルのハイパーリンクを取得し、セルにハイパーリンクがある場合は `true` とリンクアドレスが返され、それ以外の場合は `false` と空のリンクアドレスが返されます。

たとえば、`Sheet1` という名前のワークシートのハイパーリンクを `H6` セルの座標で取得します:

```go
link, target := xlsx.GetCellHyperLink("Sheet1", "H6")
```

## スタイルインデックスの取得 {#GetCellStyle}

```go
func (f *File) GetCellStyle(sheet, axis string) int
```

指定されたワークシート名 (大文字小文字の区別) とセルの座標に基づいてセルスタイルのインデックスを取得し、セルのスタイルをコピーするときに `setcellvalue` 関数を呼び出すパラメーターとして使用できるインデックスを取得します。

## セルを結合 {#MergeCell}

```go
func (f *File) MergeCell(sheet, hcell, vcell string)
```

指定されたワークシート名 (大文字小文字を区別する) とセルの座標領域に従ってセルを結合します。 たとえば、`Sheet1` という名前のワークシートの `D3:E9` 領域のセルを結合します。

```go
xlsx.MergeCell("Sheet1", "D3", "E9")
```

指定したセルの座標領域が既に存在する他の結合セルと重なっている場合、既存の結合セルは削除されます。

## セルを結合する {#GetMergeCells}

指定されたワークシート名 (大文字小文字の区別) に基づいて、すべての結合セルの座標領域と値を取得します。

```go
func (f *File) GetMergeCells(sheet string) []MergeCell
```

## コメント追加 {#AddComment}

```go
func (f *File) AddComment(sheet, cell, format string) error
```

指定されたワークシート名、セル座標、およびスタイルパラメータ (作成者とテキスト情報) に基づいて注釈を追加します。 作成者情報の最大長は 255 文字で、テキストの最大内容は 32512 文字で、その範囲を超える文字は無視されます。 たとえば、`Sheet1!$A$3` セルに注釈を追加します。

<p align="center"><img width="612" src="./images/comment.png" alt="Excel ドキュメントに注釈を追加する"></p>

```go
xlsx.AddComment("Sheet1", "A3", `{"author":"Excelize: ","text":"This is a comment."}`)
```

## コメントを得る {#GetComments}

```go
func (f *File) GetComments() (comments map[string][]Comment)
```

このメソッドを使用すると、すべてのワークシートからコメントを取得できます。

## セル式の設定 {#SetCellFormula}

```go
func (f *File) SetCellFormula(sheet, axis, formula string)
```

指定されたワークシート名 (大文字小文字の区別) とセルの設定に基づいて、セルの数式を設定します。 数式の結果は、ワークシートが Office Excel アプリケーションによって開かれたときに計算され、Excelize は現在、数式計算エンジンを提供していないため、数式の結果を計算できません。

## セル式を取得する {#GetCellFormula}

```go
func (f *File) GetCellFormula(sheet, axis string) string
```

指定されたワークシート名 (大文字小文字の区別) とセルの座標に基づいて、セルの数式を取得します。
