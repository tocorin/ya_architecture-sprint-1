### Задание 1.
Уровень 1. Проектирование

Для создания единого приложения в данном случае предпочтителен Webpack Module Federation
Вот некроторые причины:
1. Нативная поддержка Webpack: Module Federation интегрирован в Webpack, что облегчает настройку и использование в проектах, которые уже используют Webpack для сборки.
2. Динамическое подключение модулей: Module Federation позволяет динамически загружать и подключать модули из разных приложений, что упрощает процесс разбиения приложения на микро-фронтенды.
3. Шеринг зависимостей: Он позволяет делиться зависимостями между приложениями, избегая дублирования и улучшая производительность загрузки.
4. Гибкость в разработке: Module Federation предоставляет возможность разработчикам работать параллельно над отдельными модулями без жесткой привязки к единой архитектуре, что может ускорить процесс разработки.
5. Упрощенная интеграция с существующими приложениями: Процесс интеграции Module Federation в существующие приложения часто проще, чем перестройка приложения под архитектуру Single SPA.

Уровень 2. Планирование изменений

Примерные домены, которые получись из монолита:
- host (основное приложение)
- auth (пользователь, аутентификация и авторизация)
- profile (Профиль пользователя)
- cards (Карточки, нет смысла выделять лайки в отдельные фронтенды) 


Композиция осущетвляется на клиенте.
### Плюсы клиентской композиции:
1. Гибкость в разработке: Позволяет независимым командам работать над разными частями приложения без жёсткой координации.
2. Упрощённое обновление: Легче обновлять и развёртывать отдельные части приложения без необходимости полного обновления.
3. Меньшая связность: Модули могут быть более независимыми, что снижает общую сложность системы.

Выбрана runtime интеграция
### Плюсы run-time интеграции:
1. Динамическая загрузка: Возможность загружать и обновлять компоненты без перезагрузки всей страницы.
2. Гибкость: Можно легко изменять или переключать функциональность на основе условий или пользовательских данных.
3. Снижение времени развертывания: Изменения в отдельных компонентах не требуют полного развертывания приложения, что ускоряет процесс внедрения обновлений.

Получилось следующее распложение копмонентов:
### package Host (основное приложение)

- Корневой компонент App
- Компоненты Layout, Header, Footer
- Так же тут должен быть настроен роутинг

### package auth (пользователь и аутентификация)
Компоненты:
- Login
- Register
- InfoTooltip

- utils/auth.js

### package profile (профиль пользователя)

Компоненты
- EditAvatarPopup
- EditProfilePopup
- PopupWithForm

### package cards (карточки пользователя)
- AddPlacePopup
- ImagePopup
- Card
- CardList

Уровень 3

Отказался от этой фронтендерской забавы.


# Задание 2: 

[ссылка](./arch.drawio)