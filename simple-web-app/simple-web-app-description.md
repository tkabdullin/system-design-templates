# SIMPLE WEB APPLICATION WITH API GATEWAY TEMPLATES DESCRIPTION
## Компонентная диаграмма
## Диаграмма
![Компонентная диаграмма Simple Web Application with API Gateway](/out/simple-web-app/web-app-component-diagram-template/SWAwithAPIGTW-CD-Template.png)
### Описание диаграммы
Диаграмма представляет собой шаблон компонентной диаграммы для простого веб-приложения с API Gateway. 
На диаграмме продемонстирована типичная архитектура, в которой различная бизнес-логика разделена на ответственные микросервисы, а доступ к API данные сервисов подвязан через API Gateway, обеспечивая централизованный вход и управление запросами от клиента. 

### Основные элементы шаблона:
#### Client App
Клиентское приложение, которое взаимодействует с системой. Это может быть веб-браузер или мобильное приложение, которое отправляет запросы через API Gateway.
#### API Gateway
Центральный элемент архитектуры. Это точка входа для всех клиентских запросов. API Gateway маршрутизирует запросы к соответствующим микросервисам. В других случаях API Gateway может также отвечать за авторизацию, кэширование, балансировку нагрузки и мониторинг.

#### Services
##### Auth Service
Пример сервиса аутентификации, который обрабатывает проверку подлинности пользователей.
##### User Management Service
Сервис, который управляет пользователями — создание, обновление, получение информации о пользователях.
##### Business-Domain-N Logic Service
Это пример бизнес-сервиса, который отвечает за конкретную бизнес-логику. Таких сервисов может быть несколько в реальной системе, каждый с отдельной бизнес-функцией (например, управление заказами, выставление счетов и тд).

#### Auth Service External Provider
Внешний провайдер аутентификации (например, Keycloak, Active Directory или любая другая система авторизации и управления пользователями и их доступами), с которым взаимодействует сервис аутентификации для проверки учетных данных или токенов.

#### Databases (Базы данных)
##### Users Management Service Database
База данных для хранения данных о пользователях приложения.
##### Business-Domain-N Logic Service Database
База данных для хранения информации, связанной с конкретной бизнес-логикой.

### Взаимодействие между сервисами
Сервисы могут взаимодействовать друг с другом напрямую, что подразумевает обмен данными или координацию действий для выполнения комплексных бизнес-процессов с целью синхронизации данных и отсутствия необходимости реализовывать репликацию на уровне БД.

### Почему именно такое решение и шаблон
1) Каждый сервис имеет свою четкую зону ответственности и базу данных, что является стандартным подходом в микросервисной архитектуре.
2) Использование API Gateway упрощает взаимодействие клиента с системой. Все запросы проходят через один шлюз, что улучшает безопасность, масштабируемость и мониторинг системы.
3) Каждая бизнес-логика имеет свою собственную базу данных. Это снижает риски сбоев и улучшает масштабируемость, так как данные и логика одного сервиса не зависят от других.
4) В шаблоне предусмотрен пример одного бизнес-сервиса, но шаблон легко расширить добавлением новых сервисов с аналогичной структурой, что позволяет адаптировать его под более сложные системы.
5) Включение внешнего провайдера аутентификации делает систему более гибкой, особенно для приложений, которые используют несколько способов входа или имеют интеграцию с внешними системами безопасности.
6) Шаблон четко показывает, как сервисы взаимодействуют друг с другом, с базами данных и внешними системами. Это позволяет легко понять архитектуру как разработчикам, так и другим участникам проекта.

## OTHER DIAGRAMS RELATED TO THIS TOPIC