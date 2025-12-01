@startuml
skinparam rectangle {
  BackgroundColor #E8F0FE
  BorderColor #2A4B7C
}

title Горизонтальні прототипи HealthManager

rectangle "Login Screen" as Login {
  rectangle "Username Field" as User
  rectangle "Password Field" as Pass
  rectangle "Login Button" as BtnLogin
}

rectangle "Dashboard" as Dashboard {
  rectangle "Workers Health Overview" as HealthOverview
  rectangle "IoT Sensors Status" as Sensors
  rectangle "Alerts & Notifications" as Alerts
  rectangle "Quick Actions" as QuickActions
}

rectangle "Reports" as Reports {
  rectangle "Generate Report Button" as BtnReport
  rectangle "Report Filters" as ReportFilters
  rectangle "Export Options (PDF/Excel)" as Export
}

rectangle "Settings / IoT Configuration" as Settings {
  rectangle "Add Sensor" as AddSensor
  rectangle "Remove Sensor" as RemoveSensor
  rectangle "Sensor Configurations" as SensorConfig
}

Login --> Dashboard : successful login
Dashboard --> Reports : navigate to Reports
Dashboard --> Settings : navigate to Settings

@enduml
