# АРХИТЕКТУРА УСТАНОВКИ APPBASE DCM

На рисунке ниже показана основная схема архитектуры установки AppBase.

![Installation Architecture](https://github.com/CrappyCodeMaker/ECCENTEX-KNOWLEGE/blob/main/Content/1%20Start%20work/1.2%20AppBase/2.3%20INSTALLATION%20ARCHITECTURE/IMG/InstallationArchitecture.png?raw=true)

На следующей диаграмме показана высокоуровневая архитектура платформы AppBase иллюстрирующая зависимости между уровнями.
между ярусами.

![Dependencies Between Tiers](https://github.com/CrappyCodeMaker/ECCENTEX-KNOWLEGE/blob/main/Content/1%20Start%20work/1.2%20AppBase/2.3%20INSTALLATION%20ARCHITECTURE/IMG/DependenciesBetweenTiers.png?raw=true)

### УРОВЕНЬ ВЕБ-ПРИЛОЖЕНИЯ APPBASE

ВЕБ уровень AppBase - представляет узлы, на которых выполняются компоненты веб-приложения AppBase. Эти компоненты доступны для определенных пользователей.
Существует две основные части:
  * **Клиентские компоненты AppBase** _(AppBase Desktop, AppBase Application Studio, Средство просмотра документов AppBase, пакет сканирования документов AppBase, документ WebDAV AppBase)_
  * **Системные веб-службы AppBase**

Службы веб-приложений AppBase реализованы как веб-приложения / веб-службы, размещенные в информационной службе Интернета _(Internet Information Service **[IIS]**)_.


<br/>

[back to AppBase](https://github.com/CrappyCodeMaker/ECCENTEX-KNOWLEGE/blob/main/Content/1%20Start%20work/1.2%20AppBase/AppBase.md) | [back to topics](https://github.com/CrappyCodeMaker/ECCENTEX-KNOWLEGE/tree/main/Content/0%20Topics/Topics.md)