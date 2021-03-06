# Contenu

* [Introduction](README.md)
* [Utilisation basique](base/installation.md)
  * [Installation](base/installation.md#install)
  * [Mise à niveau](base/installation.md#update)
  * [Créer un document Excel](base/installation.md#NewFile)
  * [Lire un document Excel](base/installation.md#read)
  * [Ajouter un graphique au document Excel](base/installation.md#chart)
  * [Ajouter l'image au document Excel](base/installation.md#image)
* [Classeur](workbook.md)
  * [Créer un document Excel](workbook.md#NewFile)
  * [Ouvrir](workbook.md#OpenFile)
  * [Enregistrer](workbook.md#Save)
  * [Enregistrer sous](workbook.md#SaveAs)
  * [Créer une feuille de calcul](workbook.md#NewSheet)
  * [Supprimer la feuille de calcul](workbook.md#DeleteSheet)
  * [Copier la feuille de calcul](workbook.md#CopySheet)
  * [Arrière-plan de la feuille de travail](workbook.md#SetSheetBackground)
  * [Définir la feuille de calcul par défaut](workbook.md#SetActiveSheet)
  * [Obtenir l'index de feuille actif](workbook.md#GetActiveSheetIndex)
  * [Obtenir les propriétés d'affichage de la feuille de calcul](workbook.md#GetSheetViewOptions)
  * [Définir la mise en page de feuille de calcul](workbook.md#SetPageLayout)
  * [Obtenir la mise en page de feuille de calcul](workbook.md#GetPageLayout)
* [Feuille de travail](sheet.md)
  * [Définir la visibilité de la colonne](sheet.md#SetColVisible)
  * [Définir la largeur de la colonne](sheet.md#SetColWidth)
  * [Définir la hauteur de ligne](sheet.md#SetRowHeight)
  * [Définir la visibilité de la ligne](sheet.md#SetRowVisible)
  * [Obtenir le nom de la feuille de calcul](sheet.md#GetSheetName)
  * [Obtenir la visibilité de la colonne](sheet.md#GetColVisible)
  * [Obtenir la largeur de la colonne](sheet.md#GetColWidth)
  * [Obtenir la hauteur de la rangée](sheet.md#GetRowHeight)
  * [Obtenir la visibilité des lignes](sheet.md#GetRowVisible)
  * [Obtenir l'index de la feuille de calcul](sheet.md#GetSheetIndex)
  * [Obtenir la liste des feuilles de calcul](sheet.md#GetSheetMap)
  * [Obtenir les propriétés de la feuille de calcul](sheet.md#GetSheetPrOptions)
  * [Insérer une colonne](sheet.md#InsertCol)
  * [Insérer une ligne](sheet.md#InsertRow)
  * [Ajouter une ligne en double](sheet.md#DuplicateRow)
  * [Ligne en double](sheet.md#DuplicateRowTo)
  * [Créer un contour de ligne](sheet.md#SetRowOutlineLevel)
  * [Créer un plan de colonne](sheet.md#SetColOutlineLevel)
  * [Obtenir le contour de la ligne](sheet.md#GetRowOutlineLevel)
  * [Obtenir le plan de la colonne](sheet.md#GetColOutlineLevel)
  * [Row itérateur](sheet.md#Rows)
  * [Rechercher dans la fiche de calcul](sheet.md#SearchSheet)
  * [Protéger la feuille](sheet.md#ProtectSheet)
  * [Ôter la protection de la feuille](sheet.md#UnprotectedSheet)
* [Cellule](cell.md)
  * [Définir la valeur de la cellule](cell.md#SetCellValue)
  * [Définir la valeur booléenne](cell.md#SetCellBool)
  * [Définir la valeur RAW](cell.md#SetCellDefault)
  * [Définir la valeur entière](cell.md#SetCellInt)
  * [Définir la valeur de chaîne](cell.md#SetCellStr)
  * [Définir le style de cellule](cell.md#SetCellStyle)
  * [Définir un lien hypertexte](cell.md#SetCellHyperLink)
  * [Obtenir la valeur de la cellule](cell.md#GetCellValue)
  * [Obtenir toute la valeur de la cellule](cell.md#GetRows)
  * [Obtenir un lien hypertexte](cell.md#GetCellHyperLink)
  * [Obtenir l'index de style](cell.md#GetCellStyle)
  * [Fusionner les cellules](cell.md#MergeCell)
  * [Obtenir les cellules fusionnées](cell.md#GetMergeCells)
  * [Ajouter un commentaire](cell.md#AddComment)
  * [Obtenir un commentaire](cell.md#GetComments)
  * [Formule de définition de cellule](cell.md#SetCellFormula)
  * [Obtenir la formule cellulaire](cell.md#GetCellFormula)
* [Graphique](chart.md)
  * [2D graphique à aires](chart.md#area)
  * [2D graphique à aires empilées](chart.md#areaStacked)
  * [2D 100% graphique à aires empilées](chart.md#areaPercentStacked)
  * [3D graphique à aires](chart.md#area3D)
  * [3D graphique à aires empilées](chart.md#area3DStacked)
  * [3D 100% graphique à aires empilées](chart.md#area3DPercentStacked)
  * [2D graphique à barres en cluster](chart.md#bar)
  * [2D graphique à barres empilées](chart.md#barStacked)
  * [2D 100% graphique à barres empilées](chart.md#barPercentStacked)
  * [3D graphique à barres en cluster](chart.md#bar3DClustered)
  * [3D graphique à barres empilées](chart.md#bar3DStacked)
  * [3D 100% graphique à barres empilées](chart.md#bar3DPercentStacked)
  * [2D tableau à colonnes groupées](chart.md#col)
  * [2D graphique à colonnes empilées](chart.md#colStacked)
  * [2D 100% graphique à colonnes empilées](chart.md#colPercentStacked)
  * [3D tableau à colonnes groupées](chart.md#col3DClustered)
  * [3D graphique à colonnes](chart.md#col3D)
  * [3D graphique à colonnes empilées](chart.md#col3DStacked)
  * [3D 100% graphique à colonnes empilées](chart.md#col3DPercentStacked)
  * [Tableau de donut](chart.md#doughnut)
  * [Graphique en ligne](chart.md#line)
  * [Graphique tarte](chart.md#pie)
  * [3D graphique tarte](chart.md#pie3D)
  * [Graphique radar](chart.md#radar)
  * [Graphique de dispersion](chart.md#scatter)
* [Image](image.md)
  * [Ajouter une image](image.md#AddPicture)
  * [Obtenir l'image](image.md#GetPicture)
* [Forme](shape.md)
* [Style](style.md)
  * [Créer un style](style.md#NewStyle)
  * [Border](style.md#border)
  * [Couleur de remplissage](style.md#shading)
  * [Motif de remplissage](style.md#pattern)
  * [Aligner](style.md#align)
  * [Police soulignée](style.md#underline)
  * [Format de nombre](style.md#number_format)
* [Données](data.md)
  * [Validation des données](data.md#AddDataValidation)
* [Utilitaire](utils.md)
  * [Table](utils.md#AddTable)
  * [Filtre autor](utils.md#AutoFilter)
  * [Mettre à jour la valeur liée](utils.md#UpdateLinkedValue)
  * [Convertir la colonne en index](utils.md#TitleToNumber)
  * [Convertir l'index en colonne](utils.md#ToAlphaString)
  * [Style de condition](utils.md#NewConditionalStyle)
  * [Format de condition](utils.md#SetConditionalFormat)
  * [Panes](utils.md#SetPanes)
  * [Couleur](utils.md#ThemeColor)
  * [Convertir RGB en HSL](utils.md#RGBToHSL)
  * [Convertir HSL en RGB](utils.md#HSLToRGB)
  * [Writer Fichier](utils.md#FileWriter)
* [Constantes](constants.md)
* [Performance](performance.md)
* [Contribution](contribution.md)