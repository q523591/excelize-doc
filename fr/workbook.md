# Classeur

## Créer un document Excel {#NewFile}

```go
func NewFile() *File
```

NewFile fournit une fonction pour créer un nouveau fichier par le modèle par défaut. Le classeur nouvellement créé contiendra par défaut une feuille de calcul appelée `Sheet1`. Par exemple:

## Ouvrir {#OpenFile}

```go
func OpenFile(filename string) (*File, error)
```

OpenFile prend le nom d'un fichier XLSX et renvoie une structure de fichier XLSX remplie pour cela.

## Enregistrer {#Save}

```go
func (f *File) Save() error
```

Save fournit une fonction pour remplacer le fichier xlsx avec le chemin d'origine.

## Enregistrer sous {#SaveAs}

```go
func (f *File) SaveAs(name string) error
```

SaveAs fournit une fonction pour créer ou mettre à jour un fichier xlsx sur le chemin fourni.

## Créer une feuille de calcul {#NewSheet}

```go
func (f *File) NewSheet(name string) int
```

NewSheet fournit une fonction pour créer une nouvelle feuille par nom de feuille de calcul donné lors de la création d'un nouveau fichier XLSX, la feuille par défaut sera créée, lorsque vous créez un nouveau fichier.

## Supprimer la feuille de calcul {#DeleteSheet}

```go
func (f *File) DeleteSheet(name string)
```

DeleteSheet fournit une fonction pour supprimer une feuille de calcul dans un classeur par nom de feuille de calcul donné. Utilisez cette méthode avec précaution, ce qui affectera les modifications dans les références telles que les formules, les graphiques, etc. S'il y a une valeur référencée de la feuille de calcul supprimée, cela provoquera une erreur de fichier lorsque vous l'ouvrez. Cette fonction sera invalide quand seule la feuille de travail est laissée.

## Copier la feuille de calcul {#CopySheet}

```go
func (f *File) CopySheet(from, to int) error
```

CopySheet fournit une fonction pour dupliquer une feuille de calcul en donnant l'index de la feuille de calcul source et cible. Notez que les classeurs en double contenant des tableaux, des graphiques ou des images ne sont actuellement pas pris en charge. Par exemple:

```go
// Sheet1 existe déjà...
index := xlsx.NewSheet("Sheet2")
err := xlsx.CopySheet(1, index)
return err
```

## Arrière-plan de la feuille de travail {#SetSheetBackground}

```go
func (f *File) SetSheetBackground(sheet, picture string) error
```

SetSheetBackground fournit une fonction pour définir l'image d'arrière-plan par nom de feuille de calcul donné.

## Définir la feuille de calcul par défaut {#SetActiveSheet}

```go
func (f *File) SetActiveSheet(index int)
```

SetActiveSheet fournit une fonction pour définir la feuille de calcul active par défaut de XLSX par index donné. Notez que l'indice actif est différent avec l'indice qui a obtenu par la fonction [`GetSheetMap`](sheet.md#GetSheetMap), et il devrait être supérieur à `0` et moins le nombre total de feuille de calcul.

## Obtenir l'index de feuille actif {#GetActiveSheetIndex}

```go
func (f *File) GetActiveSheetIndex() int
```

GetActiveSheetIndex fournit une fonction pour obtenir une feuille active de XLSX. S'il n'est pas trouvé, la feuille active retournera l'entier `0`.

## Obtenir les propriétés d'affichage de la feuille de calcul {#GetSheetViewOptions}

```go
func (f *File) GetSheetViewOptions(name string, viewIndex int, opts ...SheetViewOptionPtr) error
```

GetSheetViewOptions obtient la valeur des options d'affichage de feuille. Le `viewIndex` peut être négatif et si c'est le cas est compté en arrière (`-1` est la dernière vue). Options disponibles:

Paramètre de vue facultatif|Type
---|---
DefaultGridColor|bool
RightToLeft|bool
ShowFormulas|bool
ShowGridLines|bool
ShowRowColHeaders|bool

- Exemple 1, pour obtenir les paramètres de la propriété gridline pour la dernière vue de la feuille de calcul nommée `Sheet1`:

```go
var showGridLines excelize.ShowGridLines
err = f.GetSheetViewOptions("Sheet1", -1, &showGridLines)
```

- Example 2:

```go
xl := excelize.NewFile()
const sheet = "Sheet1"

var (
    defaultGridColor  excelize.DefaultGridColor
    rightToLeft       excelize.RightToLeft
    showFormulas      excelize.ShowFormulas
    showGridLines     excelize.ShowGridLines
    showRowColHeaders excelize.ShowRowColHeaders
    zoomScale         excelize.ZoomScale
    topLeftCell       excelize.TopLeftCell
)

if err := xl.GetSheetViewOptions(sheet, 0,
    &defaultGridColor,
    &rightToLeft,
    &showFormulas,
    &showGridLines,
    &showRowColHeaders,
    &zoomScale,
    &topLeftCell,
); err != nil {
    panic(err)
}

fmt.Println("Default:")
fmt.Println("- defaultGridColor:", defaultGridColor)
fmt.Println("- rightToLeft:", rightToLeft)
fmt.Println("- showFormulas:", showFormulas)
fmt.Println("- showGridLines:", showGridLines)
fmt.Println("- showRowColHeaders:", showRowColHeaders)
fmt.Println("- zoomScale:", zoomScale)
fmt.Println("- topLeftCell:", `"`+topLeftCell+`"`)

if err := xl.SetSheetViewOptions(sheet, 0, excelize.TopLeftCell("B2")); err != nil {
    panic(err)
}

if err := xl.GetSheetViewOptions(sheet, 0, &topLeftCell); err != nil {
    panic(err)
}

if err := xl.SetSheetViewOptions(sheet, 0, excelize.ShowGridLines(false)); err != nil {
    panic(err)
}

if err := xl.GetSheetViewOptions(sheet, 0, &showGridLines); err != nil {
    panic(err)
}

fmt.Println("After change:")
fmt.Println("- showGridLines:", showGridLines)
fmt.Println("- topLeftCell:", topLeftCell)
```

Obtenir la sortie:

```text
Default:
- defaultGridColor: true
- rightToLeft: false
- showFormulas: false
- showGridLines: true
- showRowColHeaders: true
- zoomScale: 0
- topLeftCell: ""
After change:
- showGridLines: false
- topLeftCell: B2
```

## Définir la mise en page de feuille de calcul {#SetPageLayout}

```go
func (f *File) SetPageLayout(sheet string, opts ...PageLayoutOption) error
```

SetPageLayout fournit une fonction permettant de définir la mise en page de la feuille de calcul. Options disponibles:

- `PageLayoutOrientation` fournit une méthode pour définir l'orientation de la feuille de calcul, l'orientation par défaut est "portrait". Le tableau suivant présente les paramètres d'orientation pris en charge par le numéro d'indexation Excelize:

Paramètre | Orientation
---|---
OrientationPortrait  | portrait
OrientationLandscape | landscape

- `PageLayoutPaperSize` fournit une méthode pour définir le format de papier de la feuille de calcul. Le format de papier par défaut de la feuille de calcul est Letter US (8 1/2 × 11"). Le tableau ci-dessous présente le format de papier trié par numéro d'index Excelize:

Index | Taille de papier
---|---
1   | Letter US (8 1/2 × 11")
2   | Letter small paper (8.5 in. by 11 in.)
3   | Tabloid paper (11 in. by 17 in.)
4   | Ledger paper (17 in. by 11 in.)
5   | Legal paper (8.5 in. by 14 in.)
6   | Statement paper (5.5 in. by 8.5 in.)
7   | Executive paper (7.25 in. by 10.5 in.)
8   | A3 paper (297 mm by 420 mm)
9   | A4 paper (210 mm by 297 mm)
10  | Petit A4 (210 × 297 mm)
11  | A5 paper (148 mm by 210 mm)
12  | B4 paper (250 mm by 353 mm)
13  | B5 paper (176 mm by 250 mm)
14  | Folio paper (8.5 in. by 13 in.)
15  | Quarto paper (215 mm by 275 mm)
16  | Standard paper (10 in. by 14 in.)
17  | Standard paper (11 in. by 17 in.)
18  | Note paper (8.5 in. by 11 in.)
19  | #9 envelope (3.875 in. by 8.875 in.)
20  | #10 envelope (4.125 in. by 9.5 in.)
21  | #11 envelope (4.5 in. by 10.375 in.)
22  | #12 envelope (4.75 in. by 11 in.)
23  | #14 envelope (5 in. by 11.5 in.)
24  | C paper (17 in. by 22 in.)
25  | D paper (22 in. by 34 in.)
26  | E paper (34 in. by 44 in.)
27  | DL envelope (110 mm by 220 mm)
28  | C5 envelope (162 mm by 229 mm)
29  | C3 envelope (324 mm by 458 mm)
30  | C4 envelope (229 mm by 324 mm)
31  | C6 envelope (114 mm by 162 mm)
32  | C65 envelope (114 mm by 229 mm)
33  | B4 envelope (250 mm by 353 mm)
34  | B5 envelope (176 mm by 250 mm)
35  | B6 envelope (176 mm by 125 mm)
36  | Italy envelope (110 mm by 230 mm)
37  | Monarch envelope (3.875 in. by 7.5 in.).
38  | 6 3/4 envelope (3.625 in. by 6.5 in.)
39  | US standard fanfold (14.875 in. by 11 in.)
40  | German standard fanfold (8.5 in. by 12 in.)
41  | German legal fanfold (8.5 in. by 13 in.)
42  | ISO B4 (250 mm by 353 mm)
43  | Japanese postcard (100 mm by 148 mm)
44  | Standard paper (9 in. by 11 in.)
45  | Standard paper (10 in. by 11 in.)
46  | Standard paper (15 in. by 11 in.)
47  | Invite envelope (220 mm by 220 mm)
50  | Letter extra paper (9.275 in. by 12 in.)
51  | Legal extra paper (9.275 in. by 15 in.)
52  | Tabloid extra paper (11.69 in. by 18 in.)
53  | A4 extra paper (236 mm by 322 mm)
54  | Letter transverse paper (8.275 in. by 11 in.)
55  | A4 transverse paper (210 mm by 297 mm)
56  | Letter extra transverse paper (9.275 in. by 12 in.)
57  | SuperA/SuperA/A4 paper (227 mm by 356 mm)
58  | SuperB/SuperB/A3 paper (305 mm by 487 mm)
59  | Letter plus paper (8.5 in. by 12.69 in.)
60  | A4 plus paper (210 mm by 330 mm)
61  | A5 transverse paper (148 mm by 210 mm)
62  | JIS B5 transverse paper (182 mm by 257 mm)
63  | A3 extra paper (322 mm by 445 mm)
64  | A5 extra paper (174 mm by 235 mm)
65  | ISO B5 extra paper (201 mm by 276 mm)
66  | A2 paper (420 mm by 594 mm)
67  | A3 transverse paper (297 mm by 420 mm)
68  | A3 extra transverse paper (322 mm by 445 mm)
69  | Japanese Double Postcard (200 mm x 148 mm)
70  | A6 (105 mm x 148 mm)
71  | Japanese Envelope Kaku #2
72  | Japanese Envelope Kaku #3
73  | Japanese Envelope Chou #3
74  | Japanese Envelope Chou #4
75  | Letter Rotated (11in x 8 1/2 11 in)
76  | A3 Rotated (420 mm x 297 mm)
77  | A4 Rotated (297 mm x 210 mm)
78  | A5 Rotated (210 mm x 148 mm)
79  | B4 (JIS) Rotated (364 mm x 257 mm)
80  | B5 (JIS) Rotated (257 mm x 182 mm)
81  | Japanese Postcard Rotated (148 mm x 100 mm)
82  | Double Japanese Postcard Rotated (148 mm x 200 mm)
83  | A6 Rotated (148 mm x 105 mm)
84  | Japanese Envelope Kaku #2 Rotated
85  | Japanese Envelope Kaku #3 Rotated
86  | Japanese Envelope Chou #3 Rotated
87  | Japanese Envelope Chou #4 Rotated
88  | B6 (JIS) (128 mm x 182 mm)
89  | B6 (JIS) Rotated (182 mm x 128 mm)
90  | (12 in x 11 in)
91  | Japanese Envelope You #4
92  | Japanese Envelope You #4 Rotated
93  | PRC 16K (146 mm x 215 mm)
94  | PRC 32K (97 mm x 151 mm)
95  | PRC 32K(Big) (97 mm x 151 mm)
96  | PRC Envelope #1 (102 mm x 165 mm)
97  | PRC Envelope #2 (102 mm x 176 mm)
98  | PRC Envelope #3 (125 mm x 176 mm)
99  | PRC Envelope #4 (110 mm x 208 mm)
100 | PRC Envelope #5 (110 mm x 220 mm)
101 | PRC Envelope #6 (120 mm x 230 mm)
102 | PRC Envelope #7 (160 mm x 230 mm)
103 | PRC Envelope #8 (120 mm x 309 mm)
104 | PRC Envelope #9 (229 mm x 324 mm)
105 | PRC Envelope #10 (324 mm x 458 mm)
106 | PRC 16K Rotated
107 | PRC 32K Rotated
108 | PRC 32K(Big) Rotated
109 | PRC Envelope #1 Rotated (165 mm x 102 mm)
110 | PRC Envelope #2 Rotated (176 mm x 102 mm)
111 | PRC Envelope #3 Rotated (176 mm x 125 mm)
112 | PRC Envelope #4 Rotated (208 mm x 110 mm)
113 | PRC Envelope #5 Rotated (220 mm x 110 mm)
114 | PRC Envelope #6 Rotated (230 mm x 120 mm)
115 | PRC Envelope #7 Rotated (230 mm x 160 mm)
116 | PRC Envelope #8 Rotated (309 mm x 120 mm)
117 | PRC Envelope #9 Rotated (324 mm x 229 mm)
118 | PRC Envelope #10 Rotated (458 mm x 324 mm)

- Par exemple, définissez la mise en page pour `Sheet1` avec du papier format Petit A4 (210 × 297 mm):

```go
xl := excelize.NewFile()
const sheet = "Sheet1"

if err := xl.SetPageLayout(
    "Sheet1",
    excelize.PageLayoutOrientation(excelize.OrientationLandscape),
); err != nil {
    panic(err)
}
if err := xl.SetPageLayout(
    "Sheet1",
    excelize.PageLayoutPaperSize(10),
); err != nil {
    panic(err)
}
```

## Obtenir la mise en page de feuille de calcul {#GetPageLayout}

```go
func (f *File) GetPageLayout(sheet string, opts ...PageLayoutOptionPtr) error
```

GetPageLayout fournit une fonction pour obtenir la mise en page de la feuille de calcul. Options disponibles:

- `PageLayoutOrientation` fournit une méthode pour obtenir l'orientation de la feuille de travail
- `PageLayoutPaperSize` fournit une méthode pour obtenir le format de feuille de calcul

- Par exemple, obtenez la mise en page de `Sheet1`:

```go
xl := excelize.NewFile()
const sheet = "Sheet1"
var (
    orientation excelize.PageLayoutOrientation
    paperSize   excelize.PageLayoutPaperSize
)
if err := xl.GetPageLayout("Sheet1", &orientation); err != nil {
    panic(err)
}
if err := xl.GetPageLayout("Sheet1", &paperSize); err != nil {
    panic(err)
}
fmt.Println("Defaults:")
fmt.Printf("- orientation: %q\n", orientation)
fmt.Printf("- paper size: %d\n", paperSize)
// Output:
// Defaults:
// - orientation: "portrait"
// - paper size: 1
```
