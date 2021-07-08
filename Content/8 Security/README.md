# НАСТРОЙКА РАЗРЕШЕНИЙ

1. Переходим в Студия приложений и выбираем нужный SOLUTION
2. В сайдбаре Security => Roles

![img1](https://github.com/CrappyCodeMaker/ECCENTEX-KNOWLEGE/blob/main/Content/8%20Security/IMG/1.png?raw=true)

3. Создаем новую роль нажав New Role
4. В сайдбаре Applications => User Applications
5. В открывшемся окне кликаем нужный ресурс (ссылка на страницу) и проставляем галочки в разделе Item Permissions => Сохраняем. (Так мы обозначим какие страницы будут видны данной роле)

![img2](https://github.com/CrappyCodeMaker/ECCENTEX-KNOWLEGE/blob/main/Content/8%20Security/IMG/2.png?raw=true)

6. Далее переходим в раздел  Manage Users => User Management => Groups

![img3](https://github.com/CrappyCodeMaker/ECCENTEX-KNOWLEGE/blob/main/Content/8%20Security/IMG/3.png?raw=true)

7. Создаем необходимую группу и определяем роли которые получает эта группа


Для того чтобы управлять контекстом внутри формы, например: доступ к кнопке, скрытие панелей различных и т.д. и т.п. (если это необходимо), существует понятие Бизнес Роль. (БР)
1. Для настройки переходим в Setup солюшена => Internal People => Business Roles

![img4](https://github.com/CrappyCodeMaker/ECCENTEX-KNOWLEGE/blob/main/Content/8%20Security/IMG/4.png?raw=true)

2. Создаем необходимую БР
3. Добавляем в нее агентов, путем нажатия кнопки _Add/Remove Case Workers_

![img5](https://github.com/CrappyCodeMaker/ECCENTEX-KNOWLEGE/blob/main/Content/8%20Security/IMG/5.png?raw=true)

4. Далее в коде ограничиваем доступ к конкретному UI элементу
    * Проставляем на Panel атрибут элементу bind: {hidden: '{isExtAgent}'}
    * Сам элемент описывается во ViewModel

    * Далее в Controller сделано правило, которое обращается к БД, считывает в каких Бизнес Группах находится юзер и от этого либо скрывает либо показывает соответствующий элемент.

    * Собственно вот пример бизнес правила. Получаем ИД ЮЗЕРА, смотрим какие у него бизнес правила, и возвращает через запятую список его БР



[back to topics](https://github.com/CrappyCodeMaker/ECCENTEX-KNOWLEGE/blob/main/Content/0%20Topics/README.md)