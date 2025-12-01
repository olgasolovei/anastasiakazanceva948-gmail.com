@startuml

class User {
  - userId: int
  - username: string
  - passwordHash: string
  - role: string
  + login(): bool
  + logout(): void
}

class Worker {
  - workerId: int
  - name: string
  - position: string
  - healthStatus: string
  + updateHealthStatus(status: string): void
}

class Sensor {
  - sensorId: int
  - type: string
  - status: string
  - lastValue: float
  + readData(): float
  + calibrate(): void
}

class SensorManager {
  + addSensor(sensor: Sensor): void
  + removeSensor(sensorId: int): void
  + getSensorData(sensorId: int): float
}

class HealthAnalyzer {
  + analyze(Worker, Sensor): string
  + detectRisks(Worker): List<string>
}

class Report {
  - reportId: int
  - createdAt: datetime
  - content: string
  + exportPDF(): void
  + exportExcel(): void
}

class ReportGenerator {
  + generateForWorker(worker: Worker): Report
  + generateSummary(): Report
}

class Notification {
  - notificationId: int
  - type: string
  - text: string
  - createdAt: datetime
  + markAsRead(): void
}

class NotificationService {
  + sendAlert(worker: Worker, message: string): Notification
  + getActiveAlerts(): List<Notification>
}

class Settings {
  - configId: int
  - alertThresholds: Map
  - sensorConfig: Map
  + update(): void
}

User "1" -- "many" ReportGenerator 
User "1" -- "many" NotificationService 

Worker "1" -- "many" Sensor 
SensorManager "1" -- "many" Sensor 

HealthAnalyzer --> Worker
HealthAnalyzer --> Sensor

ReportGenerator --> Report
NotificationService --> Notification

Settings --> SensorManager
Settings --> HealthAnalyzer

@enduml
