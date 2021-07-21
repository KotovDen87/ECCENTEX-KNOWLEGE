# ⚡ РУЛЫ

1. Переходим в **`Студия приложений`** и выбираем нужный **SOLUTION**

![AppStudio](https://github.com/CrappyCodeMaker/ECCENTEX-KNOWLEGE/blob/main/Content/IMG/AppStudio.png?raw=true)

2. В сайдбаре **`Business Rules`** => **`Rules`** => ищем нужный или создаем свой, нажав **` New Rule`**

![img1](https://github.com/CrappyCodeMaker/ECCENTEX-KNOWLEGE/blob/main/Content/4%20Rules/IMG/1.png?raw=true)

3. Заполняем поля и сохраняем

![img2](https://github.com/CrappyCodeMaker/ECCENTEX-KNOWLEGE/blob/main/Content/4%20Rules/IMG/2.png?raw=true)

  * В **_`Rule Usage`_** обычно проставляем **Empty**. Ниже описание возможных значений:

  | **Rule Usage**                       | **Description**               |
  |--------------------------------------|-------------------------------|
  | Bookmark                             | This rule type is used for letter generation, email generation or th generate some other type of content. For this type, you need a template that references a bookmark. A template contains standard placeholders. Placeholders are areas that must be filled by a system with some additional information. A placeholder is then linked to the bookmark. You define a bookmark name and link it to a rule. The rule specifies how to extract the data from the system |
  | Business Constraint                  | This rule allows you to define some type of business constraint. For example, you could say that this account must contain a minimum of 10,000 dollars, or this account must have at least two customers, or this account must exist in some area or zip code. A constraint is always either True or False. The system, at runtime, calculates whether the condition is true or false. The result is always Boolean |
  | Business Event                       | Rules that interact with background processing events |
  | Business Object Attribute Constraint | Same as for BO but applies to attribute |
  | Business Object Create               |                               |
  | Business Object Delete               |                               |
  | Business Object Insert               |                               |
  | Business Object Update               |                               |
  | Business Relation Constraint         | Constrains a business Relationship. For example, you might want a Customer to Account relationship to contain no more than five accounts |
  | Business Relation Link               | Creates a link between BO     |
  | Business Relation Unlink             | Removes the link between BO   |
  | Capture                              | This rule is used for processing data that comes from outside the system. It specifies how you want to capture data and bring it into the system |
  | Empty                                | Empty rule type               |
  | Field Calculation                    | This means that you can define the logic for a specific field value calculation |
  | General                              | This is a general configurable rule type |
  | Scheduled Task                       | This rule will be used by scheduled tasks inside a task scheduler. For example, suppose a case must be processed within 30 days of a service agreement. You can schedule a task that iterates through all cases and locates any cases not processed within 30 days. If not processed within the time period. The system might send an email or other communication |
  | Workflow Activity Finalized Event    | Use this rule to create functionality when a Workflow Activity Finalize event is fired. This event occurs when work item leaves activity |
  | Workflow Activity Initialized Event  | Use this rule to create functionality when a Workflow Activity Initialize event is fired. This event occurs when work item arrives to activity |
  | Workflow Activity Rouring Event      | Use this rule to create functionality that executes when a work item moves from one Activity to another |
  | Workflow Activity Validate Send      | Use this rule to create functionality that determines and checks the criteria needed to move the work item from one Activity to another |
  | Workflow Create Workitem             | Use this rule to create functionality that executes when a work item is created |
  | Workflow Delete Workitem             | Use this rule to create functionality that executes when a work item is deleted |
  | Workflow Finalize                    | Use this rule to create functionality that executes when Workflow for specific work item is completed |
  | Workflow Initialize                  | Use this rule to create functionality that executes when Workflow for specific work item is initialized |
  | Workflow Load Workitem               | Use this rule to create functionality that executes when a work item is loaded for processing |
  | Workflow Transition Send             | Use this rule to create functionality when a Workflow Transition event is fired. This event occurs when work item is sent from one activity to another through specific transition |
  | Workflow Transition Validate Send    | Use this rule to create functionality that determines and checks the criteria needed to move a work item from one Activity to another through the selected Transition |
  | Workflow Update WorkItem             | Use this rule to create functionality that executes wen a work item is uploaded by a user or workflow |

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

**_NOTE:_** При клонирование рула или создании нового **ВАЖНО** проверить переменные, т.к. по дефолту всем проставится **_`Type = INPUT`_**, который необходимо изменить на верный вариант.

5. После всех правок делаем [ДЕПЛОЙ](https://github.com/CrappyCodeMaker/ECCENTEX-KNOWLEGE/blob/main/Content/2%20Deploy/Deploy.md)

**_NOTE:_** Если мы правим код рула, в котором не меняются переменные, как правило в 90% случаев, все будет работать **без деплоя!**


<br/>

[back to topics](https://github.com/CrappyCodeMaker/ECCENTEX-KNOWLEGE/tree/main/Content/0%20Topics/Topics.md)