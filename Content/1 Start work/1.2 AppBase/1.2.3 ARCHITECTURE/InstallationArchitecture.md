# АРХИТЕКТУРА УСТАНОВКИ APPBASE DCM

На рисунке ниже показана основная схема архитектуры установки AppBase.

![Installation Architecture](https://github.com/CrappyCodeMaker/ECCENTEX-KNOWLEGE/blob/main/Content/1%20Start%20work/1.2%20AppBase/1.2.3%20ARCHITECTURE/IMG/InstallationArchitecture.png?raw=true)

На следующей диаграмме показана высокоуровневая архитектура платформы AppBase иллюстрирующая зависимости между уровнями.

![Dependencies Between Tiers](https://github.com/CrappyCodeMaker/ECCENTEX-KNOWLEGE/blob/main/Content/1%20Start%20work/1.2%20AppBase/1.2.3%20ARCHITECTURE/IMG/DependenciesBetweenTiers.png?raw=true)

#### [УРОВЕНЬ ВЕБ-ПРИЛОЖЕНИЯ APPBASE](https://github.com/CrappyCodeMaker/ECCENTEX-KNOWLEGE/blob/main/Content/1%20Start%20work/1.2%20AppBase/2.3%20INSTALLATION%20ARCHITECTURE/SUB%20TOPICS/2.3.1.md)
#### [УРОВЕНЬ СЛУЖБ СИСТЕМНОГО ПРИЛОЖЕНИЯ APPBASE](https://github.com/CrappyCodeMaker/ECCENTEX-KNOWLEGE/blob/main/Content/1%20Start%20work/1.2%20AppBase/2.3%20INSTALLATION%20ARCHITECTURE/SUB%20TOPICS/2.3.2.md)
#### [УРОВЕНЬ ИНФРАСТРУКТУРЫ APPBASE](https://github.com/CrappyCodeMaker/ECCENTEX-KNOWLEGE/blob/main/Content/1%20Start%20work/1.2%20AppBase/2.3%20INSTALLATION%20ARCHITECTURE/SUB%20TOPICS/2.3.3.md)
#### [ЛОГИРОВАНИЕ И АУДИТ УСТАНОВКИ APPBASE](https://github.com/CrappyCodeMaker/ECCENTEX-KNOWLEGE/blob/main/Content/1%20Start%20work/1.2%20AppBase/2.3%20INSTALLATION%20ARCHITECTURE/SUB%20TOPICS/2.3.4.md)

### ИТОГИ
Исходя из выше сказанного, **архитектура AppBase** обеспечивает отказоустойчивую и высокодоступную конфигурацию, что позволяет удовлетворить следующие требования:
1. **Прерывание**. Система должна предотвращать прерывание обслуживания клиентов и потерю данных во время обычных, ремонтных и непредвиденных операций.
2. **Масштабируемость**. Система должна масштабироваться как по горизонтали, так и по вертикали для удовлетворения текущих и будущих потребностей внутренних и внешних пользователей. Система должна быть масштабируемой до **5x** и **10x** кратного увеличения количества одновременных подключений и файлов в час за счет добавления дополнительных ресурсов _(например, серверов, экземпляров, узлов, процессоров)_ к первоначально развернутой системе.
3. **Рост инфраструктуры**. Пропускная способность системы должна быть нанесена на график с учетом прогнозируемого роста и прогнозируемых требований к инфраструктуре.
4. **Балансировка нагрузки**. Система должна обрабатывать прогнозируемый рост с помощью расширяемой архитектуры, такой как балансировка нагрузки или дополнительные узлы.
5. **Правила межсетевого экрана**. Система должна предоставлять настраиваемые правила брандмауэра и конфигурацию веб-уровня _(DMZ)_, если применимо.
6. **Уровни**. Система должна быть способна поддерживать серверы приложений на уровне приложений хоста, базы данных на уровне базы данных и прокси на веб-уровне _(DMZ)_, если применимо.
7. **COTS**. Система должна быть установлена ​​и настроена в средах хоста, которые поддерживают разработку, тестирование и производственную эксплуатацию системы.
8. **Аутентификация**. Система должна позволять аутентификацию с помощью идентификатора пользователя / пароля и / или аутентификации на основе ключа.


<br/>

[back to AppBase](https://github.com/CrappyCodeMaker/ECCENTEX-KNOWLEGE/blob/main/Content/1%20Start%20work/1.2%20AppBase/AppBase.md) | [back to topics](https://github.com/CrappyCodeMaker/ECCENTEX-KNOWLEGE/tree/main/Content/0%20Topics/Topics.md)