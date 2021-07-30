# 🏗️ АРХИТЕКТУРА УСТАНОВКИ APPBASE DCM

На рисунке ниже показана основная схема архитектуры установки AppBase.

![Installation Architecture](https://github.com/CrappyCodeMaker/ECCENTEX-KNOWLEGE/blob/main/Content/1%20Start%20work/1.2%20AppBase/1.2.3%20Architecture/IMG/InstallationArchitecture.png?raw=true)

На следующей диаграмме показана высокоуровневая архитектура платформы AppBase иллюстрирующая зависимости между уровнями.

![Dependencies Between Tiers](https://github.com/CrappyCodeMaker/ECCENTEX-KNOWLEGE/blob/main/Content/1%20Start%20work/1.2%20AppBase/1.2.3%20Architecture/IMG/DependenciesBetweenTiers.png?raw=true)

#### [УРОВЕНЬ ВЕБ-ПРИЛОЖЕНИЯ APPBASE](https://github.com/CrappyCodeMaker/ECCENTEX-KNOWLEGE/blob/main/Content/1%20Start%20work/1.2%20AppBase/1.2.3%20Architecture/Tiers/2.3.1%20WEB%20Application.md#%D1%83%D1%80%D0%BE%D0%B2%D0%B5%D0%BD%D1%8C-%D0%B2%D0%B5%D0%B1-%D0%BF%D1%80%D0%B8%D0%BB%D0%BE%D0%B6%D0%B5%D0%BD%D0%B8%D1%8F-appbase)
#### [УРОВЕНЬ СЛУЖБ СИСТЕМНОГО ПРИЛОЖЕНИЯ APPBASE](https://github.com/CrappyCodeMaker/ECCENTEX-KNOWLEGE/blob/main/Content/1%20Start%20work/1.2%20AppBase/1.2.3%20Architecture/Tiers/2.3.2%20System%20Applications%20Services.md#%D1%83%D1%80%D0%BE%D0%B2%D0%B5%D0%BD%D1%8C-%D1%81%D0%BB%D1%83%D0%B6%D0%B1-%D1%81%D0%B8%D1%81%D1%82%D0%B5%D0%BC%D0%BD%D0%BE%D0%B3%D0%BE-%D0%BF%D1%80%D0%B8%D0%BB%D0%BE%D0%B6%D0%B5%D0%BD%D0%B8%D1%8F-appbase)
#### [УРОВЕНЬ ИНФРАСТРУКТУРЫ APPBASE](https://github.com/CrappyCodeMaker/ECCENTEX-KNOWLEGE/blob/main/Content/1%20Start%20work/1.2%20AppBase/1.2.3%20Architecture/Tiers/2.3.3%20Infrastructure.md#%D1%83%D1%80%D0%BE%D0%B2%D0%B5%D0%BD%D1%8C-%D0%B8%D0%BD%D1%84%D1%80%D0%B0%D1%81%D1%82%D1%80%D1%83%D0%BA%D1%82%D1%83%D1%80%D1%8B-appbase)
#### [ЛОГИРОВАНИЕ И АУДИТ УСТАНОВКИ APPBASE](https://github.com/CrappyCodeMaker/ECCENTEX-KNOWLEGE/blob/main/Content/1%20Start%20work/1.2%20AppBase/1.2.3%20Architecture/Tiers/2.3.4%20Installation%20Logging.md#%D0%BB%D0%BE%D0%B3%D0%B8%D1%80%D0%BE%D0%B2%D0%B0%D0%BD%D0%B8%D0%B5-%D0%B8-%D0%B0%D1%83%D0%B4%D0%B8%D1%82-%D1%83%D1%81%D1%82%D0%B0%D0%BD%D0%BE%D0%B2%D0%BA%D0%B8-appbase)

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

[back to AppBase](https://github.com/CrappyCodeMaker/ECCENTEX-KNOWLEGE/blob/main/Content/1%20Start%20work/1.2%20AppBase/AppBase.md#-%D0%B8%D0%BD%D1%84%D1%80%D0%B0%D1%81%D1%82%D1%80%D1%83%D0%BA%D1%82%D1%83%D1%80%D0%B0-%D0%B8-%D0%B0%D1%80%D1%85%D0%B8%D1%82%D0%B5%D0%BA%D1%82%D1%83%D1%80%D0%B0-%D1%83%D1%81%D1%82%D0%B0%D0%BD%D0%BE%D0%B2%D0%BA%D0%B8-appbase-dcm) | [back to topics](https://github.com/CrappyCodeMaker/ECCENTEX-KNOWLEGE/blob/main/Content/0%20Topics/Topics.md#-topics)