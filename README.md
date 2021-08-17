# Мониторинг составов избирательных комиссий Санкт-Петербурга

Скрипт сохраняет в текстовом файле [members.tsv](members.tsv) список членов всех избирательных комиссий Санкт-Петербурга. Данные загружаются из [ГАС Выборы](http://www.st-petersburg.vybory.izbirkom.ru/region/st-petersburg?action=ik). Каждая строка в файле соответствует одному члену какой-либо избирательной комиссии и содержит нескольких полей, разделенных символом табуляции. Перечень полей следующий:

- название избирательной комиссии (`commission_name`), например, `ТИК № 1` или `Участковая избирательная комиссия №1234`;
- название вышестоящей избирательной комиссии (`parent_commission`), пустое значение соответствует `ЦИК`;
- ФИО члена избирательной комиссии (`member_name`);
- статус члена избирательной комиссии (`member_status`): председатель, зам. пред., секретарь, член;
- кем предложен в состав комиссии (`delegated_by`), название партии, организации или объединения граждан.


Файл в формате TSV может быть открыт для просмотра и редактирования в любом табличном редакторе, например, MS Excel, OpenOffice Calc, MacOS Numbers и др. Также файл является человекочитаемым и может быть без труда открыт в любом текстовом редакторе, хоть в Блокноте.

## Отслеживание изменений
Простейший способ увидеть какие изменения произошли в составах ТИК и УИК - скачать две разных версии файла [members.tsv](members.tsv) и сравнить их с помощью любой подходящей программы. В ОС Linux для этого идеально подходят утилиты `diff` и `comm`, в ОС Windows - WinDiff, WinMerge и т.п. Выбрать нужные версии файла для сравнения можно по датам их загрузки в репозиторий. Также дата выгрузки данных из ГАС Выборы записывается в сообщение коммита.

В папке [diffs](diffs) дополнительно размещены текстовые файлы с информацией об изменениях составов нижестоящих избирательных комиссий, утвержденных соответствующей вышестоящей комиссией. Имя файла совпадает с названием комиссии, являющейся вышестоящей по отношению к той, состав которой изменился. Формат строк в текстовых файлах в папке [diffs](diffs) совпадает с описанным выше форматом файла `members.tsv`. Дополнительно в начале каждой строки стоит знак `+` или `-`. Знак `+` означает, что данный ЧПРГ был добавлен в состав комиссии, а знак `-` свидетельствует об исключении ЧПРГ.