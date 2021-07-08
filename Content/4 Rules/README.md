# РУЛЫ

1. Переходим в **`Студия приложений`** и выбираем нужный SOLUTION
2. В сайдбаре **`Business Rules`** => **`Rules`** => ищем нужный или создаем свой, нажав **` New Rule`**

![img1](https://github.com/CrappyCodeMaker/ECCENTEX-KNOWLEGE/blob/main/Content/4%20Rules/IMG/1.png?raw=true)

3. Заполняем поля и сохраняем

![img2](https://github.com/CrappyCodeMaker/ECCENTEX-KNOWLEGE/blob/main/Content/4%20Rules/IMG/2.png?raw=true)

  * В **_`Rule Usage`_** обычно проставляем **Empty**. Ниже описание возможных значений:

  | **Rule Usage** | **Description**                  |
  |----------------|----------------------------------|
  | 1          | **Bracket Pair Colorizer 2**  |
  | 2          | **CCM Oracle PL/SQL**         |
  | 3          | **CCM Theme**                 |
  | 4          | **Material Icon Theme**       |
  | 5          | **GitLens**                   |
  | 6          | **JS _(ES6)_ snippets**       |
  | 7          | **Rainbow CSV**               |
  | 8          | **Prettier** |

  * В **_`Rule Type`_** выбираем нужный нам тип рула. Ниже описание возможных значений:

  | **Rule Type** | **Description**                   |
  |---------------|---------------------------------- |
  | CSharp        | A rule written using the C# language within the Microsoft.NET Framework |
  | SQL           | This rule type operates on database tables and fields using xact names specified by SQL code. Tied to the database schema. Returns an entire set of records for a specified business entity |
  | SQL Paginated | A rule that returns a paginated set of records |
  | SQL Scalar    | A rule that returns a single value |
  | SQL Non Query | A rule that executed SQL that creates, updates, or deletes records within the database |
  | XML           | Usually for dictionaries |
  | Spring.NET    | Spring.NET is an open source application framework that promotes well established patters into building enterprise .NET applications. One of the features provided by Spring.NET is ability to setup business rules, create relevant configurations and execute those rules by means of framework |
  | Decision      | A decision rule type is used by various solution components when decision has to be made. For example, those rules may be used for workflows to determine the next Activity and participant in a workflow process. In the workflow an Activity might be linked to five subsequent Activities. The decision rule determines through which Transition and to which Activity the work item will be sent, and to which participant it will be assigned. This sending decision depends on the properties of the work item and/or related business objects  |
  | Extension     | Create a rule type based on a DLL extension that was previously registered. This rule type gives you the ability to select from a list of DLL extensions and then select a specific class and method that should be called. This rule type provides the ability to develop and invoke functionality of any complexity, or use functionality provided by third party libraries |
  | Composite     | Configures a composite wizard to create a composite rule wherein multiple rules are linked together. The final rule is generated in C# |

  * Чтобы указать, что правило является асинхронным, выберите **`Is Asynchronous`**. Это касается сценария, в котором правило может либо поддерживать соединение открытым при выполнении правила, либо обрабатывать асинхронное выполнение, не дожидаясь ожидания. Во втором сценарии обратный вызов правила выполняется, когда намеченное правило действительно выполняется.
  * Чтобы указать, что правило кэшируется, выберите **`Is cached`**.
  * Чтобы указать, что будет использоваться **Eval Body**, установите флажок **`Is Eval Body`**.
  * Чтобы указать, что правило должно быть публичным, установите флажок **`Is Public`**.
  * В поле **`Code Body`** вы вводите свой код правила. Используемый код будет зависеть от выбранного типа правила - например, если вы выбрали **SQL** в качестве типа, вам нужно будет ввести код синтаксиса **SQL** или если вы выбрали **CSharp** в качестве типа правила, вы должны ввести код на **C#**.

4. Прописываем переменные во вкладке **`Parameters`**

**_NOTE:_** При клонирование рула или создании нового проверять переменные, т.к. По дефолту всем проставится **_`Type = INPUT`_**

5. После всех правок делаем деплой

**_NOTE:_** Если мы правим код рула, в котором не меняются переменные, как правило в 90% случаев, все будет работать без деплоя!


[back to topics](https://github.com/CrappyCodeMaker/ECCENTEX-KNOWLEGE/blob/main/Content/0%20Topics/README.md)