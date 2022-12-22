# bitrix-ui.ui-grid-collapse
Расширение для добавления вложенных раскрывающихся списков в грид (Bitrix main.ui.grid)

## Использования

Размещаем расширение в папке local/ (local/js/aclips/ui-grid-collapse)

### Подготовка данных (ROWS bitrix:main.ui.grid)

**Элементы должны идти в строгой последовательнисти отображения**

При формировании данныхдля списка всем элементам, которые являются разделами нужно добавить аттрибут

```php
...
if($isSection) {
    $row['attrs']['is-section'] = true;
}
...
```

Добавляем аттрибут идентифицирующий принадлежность к разделу для элементов 
являющихся вложенным в раздел (вложенность разделов поддерживается).

```php
...
if($existParentId){
    $row['attrs']['parent'] = $parentId;
}
...
```

### Инициализация плангина

```javascript
<?php \Bitrix\Main\UI\Extension::load('aclips.ui-grid-collapse') ?>

<script>
    BX.ready(function () {
            BX.Aclips.Plugin.UIGridCollapse.initCollapse('Идентификатор грида (GRID_ID)', {
                'default-collapse': true,
                'is-section-selector': '[is-head="true"]',
                'parent-attribute': 'parent'
            })
        }
    );
</script>
```

Результат

![Результат](https://github.com/aclips/bitrix-ui.ui-grid-collapse/blob/main/example.jpg)
