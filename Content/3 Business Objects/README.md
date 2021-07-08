# БИЗНЕС ОБЪЕКТЫ

1. Переходим в **`Студия приложений`** и выбираем нужный SOLUTION
2. В сайдбаре **`Data management`** => **`Business Objects`** => ищем нужный или создаем свой, нажав **`New Business Objects`**

![Preview](https://github.com/CrappyCodeMaker/ECCENTEX-KNOWLEGE/blob/main/Content/2%20Deploy/IMG/1.png?raw=true)

**_NOTE:_**
  * Связь с другой таблицей можно настроить на вкладке **`Relationships`** _(Отношения)_
  * Если необходимо изменить тип атрибута, то просто поменять его невозможно. Для изменения типа необходимо понять если какие-либо данные в данном атрибуте (колонка таблицы):

  1. _`ДАННЫЕ ЕСТЬ:`_

      * **СПОСОБ 1:** Создать новый атрибут _(временный)_. Задеплоить изменение. В БД перенести данные из текущей колонки во временную. Удалить старый атрибут и создать новый с тем же названием и новым типом. Задеплоить изменение. Перенести данные в корректный атрибут. Удалить временный. Задеплоить.

      * **СПОСОБ 2:** Создаем темповую таблицу и апдейтим колонку в исходной таблице в **NULL**. Удаляем атрибут и создаем новый, с нужным типом данных. Деплоим. Заливаем данные обратно.

```SQL
    --Создаем ТМП таблицу
    create table TEST_TMP as (select col_id, column_1 from ORIGIN_TABLE)

    --Заливаем данные обратно
    MERGE INTO ORIGIN_TABLE ORIG
      USING (SELECT tmp.col_id, tmp.column_1 FROM TEST_TMP tmp) MRG
      ON (ORIG.col_id = MRG.col_id)
    WHEN MATCHED THEN
	    UPDATE SET ORIG.column_1 = MRG.column_1
```

  2. _`ДАННЫХ НЕТ:`_ Удаляем старый атрибут. Создаем новый. Деплоим


[back to topics](https://github.com/CrappyCodeMaker/ECCENTEX-KNOWLEGE/blob/main/Content/0%20Topics/README.md)