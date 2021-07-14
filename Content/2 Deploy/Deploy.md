# ДЕПЛОЙ

1. Переходим в **`Студия приложений`** и выбираем нужный **SOLUTION**

![AppStudio](https://github.com/CrappyCodeMaker/ECCENTEX-KNOWLEGE/blob/main/Content/IMG/AppStudio.png?raw=true)

2. В сайдбаре **`Deployment management`** => **`Dtploy`** => нажимаем **`Preview`** и ждем

![img1](https://github.com/CrappyCodeMaker/ECCENTEX-KNOWLEGE/blob/main/Content/2%20Deploy/IMG/1.png?raw=true)

3. После завершения **`Preview`** станет доступна кнопка **`Execute SQL`**. Кликаем по этой кнопке и ждем.

**_NOTE:_** _Если вы удаляли что-либо, например, атрибут в БО, под кнопкой **`Execute SQL`** появится инпут в который нужно будет вписать **`DELETE`**._

**_NOTE:_** **`Execute SQL`** _присутствует только на_ **DEV** _среде. На_ **PROD** _и_ **QA** _средах после_ п.2 _переходим к_ п.4

**_NOTE:_** В **`Journal`** **_(Журнале)_** _перечислены все изменения, попавшие в текущий деплой_

![img2](https://github.com/CrappyCodeMaker/ECCENTEX-KNOWLEGE/blob/main/Content/2%20Deploy/IMG/2.png?raw=true)

4. Если все прошло без ошибок далее станет доступна кнопка **`CONFIRM`** => Кликаем по этой кнопке и ждем.
5. Деплой будет завершен, когда вы увидите следующую запись:

  * для **DEV**

![img3](https://github.com/CrappyCodeMaker/ECCENTEX-KNOWLEGE/blob/main/Content/2%20Deploy/IMG/3a.png?raw=true)

  * для **PROD** и **QA**

![img3](https://github.com/CrappyCodeMaker/ECCENTEX-KNOWLEGE/blob/main/Content/2%20Deploy/IMG/3b.png?raw=true)

**_NOTE:_** _Если вы хотите задеплоить правки и при переходе в раздел деплоя вылетает окно с предложением **приджойнится**, хорошим тоном является решение_ **НЕ ДЖОЙНИТЬСЯ** _и подождать пока другой разработчик завершит деплой. В противном случае, приджойнившись вы можете раньше нажать **`Confirm` _(Apply Changes)_**, в этом случае у другого разработчика вылетит ошибка, при клике. У разработчика начнется паника из-за ошибки, потому что он не будет знать что кто-то другой завершил его деплой_ 😃

  ![img4a](https://github.com/CrappyCodeMaker/ECCENTEX-KNOWLEGE/blob/main/Content/2%20Deploy/IMG/4a.png?raw=true)
  ![img4b](https://github.com/CrappyCodeMaker/ECCENTEX-KNOWLEGE/blob/main/Content/2%20Deploy/IMG/4b.png?raw=true)


<br/>

[back to topics](https://github.com/CrappyCodeMaker/ECCENTEX-KNOWLEGE/blob/main/Content/0%20Topics/README.md)