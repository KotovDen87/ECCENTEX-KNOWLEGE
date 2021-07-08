# НАСТРОЙКА РАЗРЕШЕНИЙ

1. Переходим в **`Студия приложений`** и выбираем нужный SOLUTION
2. В сайдбаре **`Security`** => **`Roles`**

![img1](https://github.com/CrappyCodeMaker/ECCENTEX-KNOWLEGE/blob/main/Content/8%20Security/IMG/1.png?raw=true)

3. Создаем новую роль нажав **`New Role`**
4. В сайдбаре **`Applications`** => **`User Applications`**
5. В открывшемся окне кликаем нужный ресурс _(ссылка на страницу)_ и проставляем галочки в разделе **`Item Permissions`** => **Сохраняем**. _(Так мы обозначим какие страницы будут видны данной роле)_

![img2](https://github.com/CrappyCodeMaker/ECCENTEX-KNOWLEGE/blob/main/Content/8%20Security/IMG/2.png?raw=true)

6. Далее переходим в раздел **`Manage Users`** => **`User Management`** => **`Groups`**

![img3](https://github.com/CrappyCodeMaker/ECCENTEX-KNOWLEGE/blob/main/Content/8%20Security/IMG/3.png?raw=true)

7. Создаем необходимую группу и определяем роли которые получает эта группа


<br/>

Для того чтобы управлять контекстом внутри формы, например: доступ к кнопке, скрытие панелей различных и т.д. и т.п. _(если это необходимо)_, существует понятие **`Бизнес Роль`**. **_(БР)_**

1. Для настройки переходим в **`Setup`** солюшена => **`Internal People`** => **`Business Roles`**

![img4](https://github.com/CrappyCodeMaker/ECCENTEX-KNOWLEGE/blob/main/Content/8%20Security/IMG/4.png?raw=true)

2. Создаем необходимую БР
3. Добавляем в нее агентов, путем нажатия кнопки **`Add/Remove Case Workers`**

![img5](https://github.com/CrappyCodeMaker/ECCENTEX-KNOWLEGE/blob/main/Content/8%20Security/IMG/5.png?raw=true)

4. Далее в коде ограничиваем доступ к конкретному UI элементу:
  * Проставляем на Panel атрибут элементу bind:
```JavaScript
    {hidden: '{isExtAgent}'}
```
  * Сам элемент описывается во **`ViewModel`**
```JavaScript
    Ext.define('SD.view.ExternalParty.Individual.ViewModel', {
        extend: 'Ext.app.ViewModel',
        alias: 'viewmodel.IndividualViewModel',
        requires: [ 'SD.model.SDDict', 'SD.model.Individual', 'SD.model.AddressExternalParties', 'SD.model.PartyType' ],
        data: {
            searchIndividual: null, isEditable: false, isExtAgent: false,
            current: {Individual: null, editMode: 'Modify'}
        },
```
  * Далее в **`Controller`** сделано правило, которое обращается к БД, считывает в каких Бизнес Группах находится юзер и от этого либо скрывает либо показывает соответствующий элемент.
```JavaScript
    if (Ext.isEmpty(roles)) {
      EcxUtils5.Request.executeRule('ROOT_SD_CHECKBUSINESSROLE', null , function (response, options, srd) {
              var result = srd.parsedData.ROLES;
              if (result.indexOf('CLL_AGENT', 0) >= 0) vm.set('isAgent', 1);
              if (result.indexOf('CLL_EXTAGENT', 0) >= 0) {
                  vm.set('isAgent', 1);
                  vm.set('isExtAgent', 1);
              }
              sessionStorage.setItem('IndividualRoles',result);
          }
          , null, {preventParentCallback: true});
    }
```
  * Собственно вот пример бизнес правила. Получаем ИД ЮЗЕРА, смотрим какие у него бизнес правила, и возвращает через запятую список его БР
```SQL
    DECLARE
      v_CaseWorkerId  INTEGER;
        v_result      INTEGER;
    BEGIN
      v_CaseWorkerId := f_DCM_getCaseWorkerId();
      IF (:BusinessRole IS NOT NULL) THEN
          SELECT COUNT(*) INTO v_result FROM (
              SELECT br.COL_CODE FROM TBL_CASEWORKERBUSINESSROLE cw_br
                INNER JOIN TBL_PPL_BUSINESSROLE br ON br.COL_ID = cw_br.COL_TBL_PPL_BUSINESSROLE
              WHERE cw_br.COL_BR_PPL_CASEWORKER = v_CaseWorkerId AND br.COL_CODE = :BusinessRole
            );
      ELSE
          SELECT LISTAGG(br.COL_CODE, ', ') WITHIN GROUP (ORDER BY  br.COL_CODE ) INTO :Roles
          FROM TBL_CASEWORKERBUSINESSROLE cw_br
            INNER JOIN TBL_PPL_BUSINESSROLE br ON br.COL_ID = cw_br.COL_TBL_PPL_BUSINESSROLE
          WHERE cw_br.COL_BR_PPL_CASEWORKER = v_CaseWorkerId;
      END IF;
      :Roles := nvl(:Roles,'*');
      :OutputValue := v_result;
    END;
```


[back to topics](https://github.com/CrappyCodeMaker/ECCENTEX-KNOWLEGE/blob/main/Content/0%20Topics/README.md)