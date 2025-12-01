@startuml
left to right direction
skinparam packageStyle rectangle

actor "Майстер будівельної ділянки" as Master
actor "Менеджер з охорони праці" as Manager
actor "Інженер IoT / Адміністратор системи" as Engineer

package "HealthManager" {
    usecase "UC-01: Моніторинг стану здоров’я" as UC01
    usecase "UC-02: Миттєві сповіщення про ризики" as UC02
    usecase "UC-03: Аналіз історії інцидентів" as UC03
    usecase "UC-04: Формування звітів" as UC04
    usecase "UC-05: Налаштування та інтеграція IoT" as UC05
    usecase "UC-06: Контроль працездатності сенсорів" as UC06
}


Master --> UC01
Master --> UC02

Manager --> UC03
Manager --> UC04

Engineer --> UC05
Engineer --> UC06


UC01 --> UC02 : <<include>>   ' Моніторинг включає отримання сповіщень
UC05 --> UC06 : <<include>>   ' Налаштування сенсорів включає контроль їх працездатності

@enduml
