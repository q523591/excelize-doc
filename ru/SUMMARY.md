# Содержание

* [Введение](README.md)
* [Основное использование](base/installation.md)
  * [Установка](base/installation.md#install)
  * [Обновление](base/installation.md#update)
  * [Создать документ Excel](base/installation.md#NewFile)
  * [Чтение документа Excel](base/installation.md#read)
  * [Добавить диаграмму в документ Excel](base/installation.md#chart)
  * [Добавить изображение в документ Excel](base/installation.md#image)
* [Рабочая книга](workbook.md)
  * [Создать документ Excel](workbook.md#NewFile)
  * [Открыть](workbook.md#OpenFile)
  * [Сохранить](workbook.md#Save)
  * [Сохранить как](workbook.md#SaveAs)
  * [Создать рабочий лист](workbook.md#NewSheet)
  * [Удалить рабочий лист](workbook.md#DeleteSheet)
  * [Лист копирования](workbook.md#CopySheet)
  * [Фон рабочего листа](workbook.md#SetSheetBackground)
  * [Установить рабочий лист по умолчанию](workbook.md#SetActiveSheet)
  * [Получить активный индекс листа](workbook.md#GetActiveSheetIndex)
  * [Получить свойства вида листа](workbook.md#GetSheetViewOptions)
  * [Установить макет страницы листа](workbook.md#SetPageLayout)
  * [Получить макет страницы листа](workbook.md#GetPageLayout)
* [Рабочий лист](sheet.md)
  * [Установить видимость столбца](sheet.md#SetColVisible)
  * [Установить ширину столбца](sheet.md#SetColWidth)
  * [Установить высоту строки](sheet.md#SetRowHeight)
  * [Установить видимость линии](sheet.md#SetRowVisible)
  * [Получить имя листа](sheet.md#GetSheetName)
  * [Получить видимость столбца](sheet.md#GetColVisible)
  * [Получить ширину столбца](sheet.md#GetColWidth)
  * [Получить высоту строки](sheet.md#GetRowHeight)
  * [Получить видимость строки](sheet.md#GetRowVisible)
  * [Получить индекс рабочего листа](sheet.md#GetSheetIndex)
  * [Получить список рабочих листов](sheet.md#GetSheetMap)
  * [Получить свойства листа](sheet.md#GetSheetPrOptions)
  * [Вставить столбец](sheet.md#InsertCol)
  * [Вставить строку](sheet.md#InsertRow)
  * [Добавить дубликат строки](sheet.md#DuplicateRow)
  * [Дублирующая строка](sheet.md#DuplicateRowTo)
  * [Создать схему строки](sheet.md#SetRowOutlineLevel)
  * [Создать контур столбца](sheet.md#SetColOutlineLevel)
  * [Получить контур линии](sheet.md#GetRowOutlineLevel)
  * [Получить контур колонны](sheet.md#GetColOutlineLevel)
  * [Ряд итератора](sheet.md#Rows)
  * [Поиск на листе](sheet.md#SearchSheet)
  * [Защитить лист](sheet.md#ProtectSheet)
  * [Снять защиту листа](sheet.md#UnprotectSheet)
* [клетка](cell.md)
  * [Установить значение ячейки](cell.md#SetCellValue)
  * [Установить логическое значение](cell.md#SetCellBool)
  * [Установить значение RAW](cell.md#SetCellDefault)
  * [Установить целочисленное значение](cell.md#SetCellInt)
  * [Установить строковое значение](cell.md#SetCellStr)
  * [Установить стиль ячейки](cell.md#SetCellStyle)
  * [Установить гиперссылку](cell.md#SetCellHyperLink)
  * [Получить значение ячейки](cell.md#GetCellValue)
  * [Получить все значения ячейки](cell.md#GetRows)
  * [Получить гиперссылку](cell.md#GetCellHyperLink)
  * [Получить индекс стиля](cell.md#GetCellStyle)
  * [Объединить ячейки](cell.md#MergeCell)
  * [Получить ячейки слияния](cell.md#GetMergeCells)
  * [Добавить комментарий](cell.md#AddComment)
  * [Получить комментарий](cell.md#GetComments)
  * [Установить формулу ячейки](cell.md#SetCellFormula)
  * [Получить формулу ячейки](cell.md#GetCellFormula)
* [Диаграмма](chart.md)
  * [2D диаграмма области](chart.md#area)
  * [2D диаграмма области с накоплением](chart.md#areaStacked)
  * [2D 100% диаграмма области с накоплением](chart.md#areaPercentStacked)
  * [3D диаграмма области](chart.md#area3D)
  * [3D диаграмма области с накоплением](chart.md#area3DStacked)
  * [3D 100% диаграмма области с накоплением](chart.md#area3DPercentStacked)
  * [2D кластерная гистограмма](chart.md#bar)
  * [2D Двухстрочная гистограмма](chart.md#barStacked)
  * [2D 100% сложная гистограмма](chart.md#barPercentStacked)
  * [3D кластерная гистограмма](chart.md#bar3DClustered)
  * [3D гистограмма](chart.md#bar3DStacked)
  * [3D 100% сложная гистограмма](chart.md#bar3DPercentStacked)
  * [2D группированная диаграмма столбцов](chart.md#col)
  * [2D сложены диаграммы колонки](chart.md#colStacked)
  * [2D 100% сложены диаграммы колонки](chart.md#colPercentStacked)
  * [3D группированная диаграмма столбцов](chart.md#col3DClustered)
  * [3D диаграмма столбца](chart.md#col3D)
  * [3D сложены диаграммы колонки](chart.md#col3DStacked)
  * [3D 100% сложены диаграммы колонки](chart.md#col3DPercentStacked)
  * [диаграмма пончика](chart.md#doughnut)
  * [линейный график](chart.md#line)
  * [круговая диаграмма](chart.md#pie)
  * [3D круговая диаграмма](chart.md#pie3D)
  * [радиолокационная карта](chart.md#radar)
  * [Точечная диаграмма](chart.md#scatter)
* [Изображение](image.md)
  * [Добавить изображение](image.md#AddPicture)
  * [Получить изображение](image.md#GetPicture)
* [форма](shape.md)
* [Стиль](style.md)
  * [Создать стиль](style.md#NewStyle)
  * [бордюр](style.md#border)
  * [Цвет заливки](style.md#shading)
  * [образец заливки](style.md#pattern)
  * [Выровнять](style.md#align)
  * [Подчеркивание шрифта](style.md#underline)
  * [Формат номера](style.md#number_format)
* [Данные](data.md)
  * [Проверка данных](data.md#AddDataValidation)
* [Функция инструмента](utils.md)
  * [Таблица](utils.md#AddTable)
  * [Авто фильтр](utils.md#AutoFilter)
  * [Обновить связанное значение](utils.md#UpdateLinkedValue)
  * [Преобразование столбца в индекс](utils.md#TitleToNumber)
  * [Преобразовать индекс в столбец](utils.md#ToAlphaString)
  * [Стиль стиля](utils.md#NewConditionalStyle)
  * [Формат условия](utils.md#SetConditionalFormat)
  * [панель](utils.md#SetPanes)
  * [Цвет](utils.md#ThemeColor)
  * [Преобразование RGB в HSL](utils.md#RGBToHSL)
  * [Конвертировать HSL в RGB](utils.md#HSLToRGB)
  * [Файловый писатель](utils.md#FileWriter)
* [Константы](constants.md)
* [Производительность](performance.md)
* [Вклад](contribution.md)