## Welcome to GitHub Pages

You can use the [editor on GitHub](https://github.com/44heroh/blogmitrex/edit/master/README.md) to maintain and preview the content for your website in Markdown files.

Whenever you commit to this repository, GitHub Pages will run [Jekyll](https://jekyllrb.com/) to rebuild the pages in your site, from the content in your Markdown files.

### Markdown

Markdown is a lightweight and easy-to-use syntax for styling your writing. It includes conventions for

```markdown
Syntax highlighted code block

# Header 1
## Header 2
### Header 3

- Bulleted
- List

1. Numbered
2. List

**Bold** and _Italic_ and `Code` text

[Link](url) and ![Image](src)
```

For more details see [GitHub Flavored Markdown](https://guides.github.com/features/mastering-markdown/).

###Проставление символьного кода у уже существующих элементов

//Для разделов 
$arFilter = Array("IBLOCK_ID"=>29); //свой ID инфоблока
$db_list = CIBlockSection::GetList(Array(), $arFilter, false);
while($ar_result = $db_list->GetNext()){
   $params = Array(
      "max_len" => "75", // обрезает символьный код до 75 символов
      "change_case" => "L", // буквы преобразуются к нижнему регистру
      "replace_space" => "-", // меняем пробелы на нижнее подчеркивание
      "replace_other" => "-", // меняем левые символы на нижнее подчеркивание
      "delete_repeat_replace" => "true", // удаляем повторяющиеся нижние подчеркивания
      "use_google" => "false", // отключаем использование google
   );
   $CODE_translit = CUtil::translit($ar_result["NAME"], "ru", $params);
   
   $bs = new CIBlockSection;

   $arFields = Array(
     "CODE" => $CODE_translit
   );
   
   $SECTION_ID = $ar_result['ID'];
   $res_upd_sec = $bs->Update($SECTION_ID, $arFields);
}

//Для элементов
$arFilter = Array("IBLOCK_ID"=>29); //свой ID инфоблока
$arSelect = Array("ID", "NAME");
$res = CIBlockElement::GetList(Array(), $arFilter, false, false, $arSelect);
while($ob = $res->GetNextElement()){
   $ccc++;
   $arFieldsElement = $ob->GetFields();

   $params = Array(
      "max_len" => "75", // обрезает символьный код до 75 символов
      "change_case" => "L", // буквы преобразуются к нижнему регистру
      "replace_space" => "-", // меняем пробелы на нижнее подчеркивание
      "replace_other" => "-", // меняем левые символы на нижнее подчеркивание
      "delete_repeat_replace" => "true", // удаляем повторяющиеся нижние подчеркивания
      "use_google" => "false", // отключаем использование google
   );
   $CODE_translit = CUtil::translit($arFieldsElement["NAME"], "ru", $params);
   
   $el = new CIBlockElement;

   $arLoadProductArray = Array(
     "CODE" => $CODE_translit
   );
   
   $PRODUCT_ID = $arFieldsElement['ID'];  // изменяем элемент с кодом (ID)
   $res_upd_el = $el->Update($PRODUCT_ID, $arLoadProductArray);
}
