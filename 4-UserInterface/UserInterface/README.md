@startuml
skinparam rectangle {
  BackgroundColor #F0F4F8
  BorderColor #2A4B7C
}
skinparam note {
  BackgroundColor #FFFACD
  BorderColor #2A4B7C
}

title Проект каркасу HealthManager


rectangle "Login Screen" as Login {
  rectangle "Username Field" as User
  rectangle "Password Field" as Pass
  rectangle "Login Button" as BtnLogin
}

note right of Login
Користувач вводить логін і пароль.
При успішній аутентифікації переходить на Dashboard.
end note


rectangle "Dashboard" as Dashboard {
  rectangle "Workers Health Overview" as HealthOverview
  rectangle "IoT Sensors Status" as Sensors
  rectangle "Alerts & Notifications" as Alerts
  rectangle "Quick Actions" as QuickActions
  rectangle "Reports Button" as BtnReports
  rectangle "Settings Button" as BtnSettings
}

note right of Dashboard
Основний екран користувача.
Доступ до всіх функцій системи: моніторинг здоров'я,
сповіщення, швидкі дії, перехід до звітів та налаштувань.
end note


rectangle "Reports Screen" as Reports {
  rectangle "Select Report Period" as ReportPeriod
  rectangle "Select Filters" as ReportFilters
  rectangle "Generate Report Button" as BtnGenerateReport
  rectangle "Export Options" as Export
}

note right of Reports
Користувач може генерувати звіти за періодами та підрозділами,
експортувати у PDF або Excel.
end note


rectangle "Settings / IoT Configuration" as Settings {
  rectangle "Add Sensor" as AddSensor
  rectangle "Remove Sensor" as RemoveSensor
  rectangle "Sensor Configurations" as SensorConfig
}

note right of Settings
Користувач-інженер може додавати, видаляти сенсори,
налаштовувати конфігурації IoT-пристроїв.
end note


Login --> Dashboard : успішний вхід
Dashboard --> Reports : натискає "Reports Button"
Dashboard --> Settings : натискає "Settings Button"
Reports --> Dashboard : натискає "Back to Dashboard"
Settings --> Dashboard : натискає "Back to Dashboard"

@enduml








# Проект макету HealthManager

## NFR_1: Login Screen
- **Елементи:**
  - Поле введення Username
  - Поле введення Password
  - Кнопка Login
  - Лінк "Forgot password?"
- **Опис зовнішнього вигляду:**
  - Центральне розташування форми на екрані
  - Сині кнопки з білим текстом
  - Лаконічний фон без графіки
- **Примітки:** Макет адаптивний для десктопа та мобільного пристрою

---

## NFR_2: Dashboard
- **Елементи:**
  - Панель навігації зліва: Dashboard, Reports, Settings
  - Блок "Workers Health Overview" з таблицею станів
  - Блок "IoT Sensors Status" з індикаторами онлайн/офлайн
  - Блок "Alerts & Notifications" з кольоровими іконками ризиків
  - Блок "Quick Actions" з кнопками для швидких дій (додати сенсор, сповіщення)
- **Опис зовнішнього вигляду:**
  - Використання кольорових статусів: зелений – нормально, жовтий – попередження, червоний – критично
  - Карточки з даними мають легку тінь для виділення
  - Інтерактивні графіки з підказками при наведенні
- **Примітки:** Dashboard має бути адаптивним та легко масштабуватися під різні розділи

---

## NFR_3: Reports Screen
- **Елементи:**
  - Випадаючі меню для вибору періоду та підрозділу
  - Кнопка Generate Report
  - Кнопка Export (PDF, Excel)
  - Таблиця результатів з сортуванням і пагінацією
- **Опис зовнішнього вигляду:**
  - Чітка структура: фільтри зверху, результати нижче
  - Використання сірого та білого фону для покращення читаності таблиць
  - Кнопки яскраво-сині, виділені при наведенні
- **Примітки:** Підтримка інтерактивних графіків для аналітики

---

## NFR_4: Settings / IoT Configuration
- **Елементи:**
  - Список сенсорів з індикаторами стану
  - Кнопки Add Sensor, Remove Sensor
  - Панель конфігурацій сенсора з полями налаштувань
  - Зберегти / Відмінити зміни
- **Опис зовнішнього вигляду:**
  - Таблиця сенсорів із сортуванням та пошуком
  - Кнопки яскраво-сині з білим текстом
  - Поля конфігурацій з підказками та випадаючими меню
- **Примітки:** Макет повинен підтримувати швидке налаштування сенсорів без переривання роботи системи

---

## NFR_5: Alerts & Notifications Panel
- **Елементи:**
  - Список активних сповіщень з іконками ризику
  - Фільтри за типом сповіщення та пріоритетом
  - Кнопка Mark as Read
  - Відображення часу надходження сповіщення
- **Опис зовнішнього вигляду:**
  - Кольорове кодування: червоний – критично, жовтий – попередження, синій – інформація
  - Панель має бути доступною з Dashboard
  - Повідомлення з можливістю розгортання для деталей
- **Примітки:** Повинна забезпечувати миттєве реагування користувача

---

## NFR_6: User Profile / Security Settings
- **Елементи:**
  - Поля для редагування профілю користувача
  - Налаштування паролю та двофакторної аутентифікації
  - Кнопки Save / Cancel
- **Опис зовнішнього вигляду:**
  - Простий, мінімалістичний макет
  - Поля з підказками
  - Кнопки яскраво-сині, активні при заповненні всіх обов’язкових полів
- **Примітки:** Макет підтримує високу безпеку та доступність користувача
