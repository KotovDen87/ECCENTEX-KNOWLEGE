# ПОЛНЫЙ ПЕРЕНОС

1. Переходим в **`Setup`** солюшена

![SolutionSetup](https://github.com/CrappyCodeMaker/ECCENTEX-KNOWLEGE/blob/main/Content/IMG/SolutionSetup.png?raw=true)

2. В Сайдбаре **`Advanced Setup`** => **`Maintenance`**. Ставим галку **Export solution** и **Full**. После этого жмем _`EXPORT`_

**_NOTE:_** _Во время ЭКСПОРТА никто не должен деплоиться!_

![img1](https://github.com/CrappyCodeMaker/ECCENTEX-KNOWLEGE/tree/main/Content/10%20Move%20Full//IMG/1.png?raw=true)

3. Качаем сформированный файл

![img2](https://github.com/CrappyCodeMaker/ECCENTEX-KNOWLEGE/tree/main/Content/10%20Move%20Full//IMG/2.png?raw=true)

4. Переходим на ту среду, куда будем делать перенос => далее в **`System Setup Home`**

![SystemSetupHome](https://github.com/CrappyCodeMaker/ECCENTEX-KNOWLEGE/blob/main/Content/IMG/SystemSetupHome.png?raw=true)

5. В сайдбаре **`Solutions`** => Кликаем **`IMPORT`** нужному солюшену

**_NOTE:_** _Во время ЭКСПОРТА никто не должен деплоиться!_

![img3](https://github.com/CrappyCodeMaker/ECCENTEX-KNOWLEGE/tree/main/Content/10%20Move%20Full//IMG/3.png?raw=true)

5. В открывшемся окне кликаем **`Upload file`** => далее **`Select file to upload`** и выбираем полученный ранее файл **(п.3)**

![img4](https://github.com/CrappyCodeMaker/ECCENTEX-KNOWLEGE/tree/main/Content/10%20Move%20Full//IMG/4.png?raw=true)

6. Снимаем галку с **`Import solution events`**, в инпуте пишем **`IMPORT`** => кликаем **`Import uploaded file`**

**_NOTE:_** _Этот шаг может занимать 15-60 минут. Не закрывайте и не перезагружайте страницу!_

![img5](https://github.com/CrappyCodeMaker/ECCENTEX-KNOWLEGE/tree/main/Content/10%20Move%20Full//IMG/5.png?raw=true)

7. После успешной загрузки кликаем **`CONFIRM`** и ждем

**_NOTE:_** _этот шаг может занимать 20-50 минут_

![img6](https://github.com/CrappyCodeMaker/ECCENTEX-KNOWLEGE/tree/main/Content/10%20Move%20Full//IMG/6.png?raw=true)

8. После появится всплывающее окно кликаем **`YES`**

![img7](https://github.com/CrappyCodeMaker/ECCENTEX-KNOWLEGE/tree/main/Content/10%20Move%20Full//IMG/7.png?raw=true)

9. После подтверждения делаем [деплой](https://github.com/CrappyCodeMaker/ECCENTEX-KNOWLEGE/blob/main/Content/2%20Deploy/README.md) солюшена
10. Кроме того, необходимо импортировать конфигурацию DCM. Откройте **DEV** солюшен => **`Export/Import`** => выберите конфигурацию «`DCM Update Export No Dict`» и нажмите **`Export selected`**.

![img8](https://github.com/CrappyCodeMaker/ECCENTEX-KNOWLEGE/tree/main/Content/10%20Move%20Full//IMG/8.png?raw=true)

11. Далее откройте солюшен на который делается перенос => **`Export/Import`** => нажмите **`Import From file`** => выберите полученный ранее архив

![img9](https://github.com/CrappyCodeMaker/ECCENTEX-KNOWLEGE/tree/main/Content/10%20Move%20Full//IMG/9.png?raw=true)

12. Если вы видите следующее, Экспорт/Импорт успешно завершен!

![img10](https://github.com/CrappyCodeMaker/ECCENTEX-KNOWLEGE/tree/main/Content/10%20Move%20Full//IMG/10.png?raw=true)


<br/>

[back to topics](https://github.com/CrappyCodeMaker/ECCENTEX-KNOWLEGE/blob/main/Content/0%20Topics/README.md)