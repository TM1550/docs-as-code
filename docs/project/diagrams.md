# Диаграммы

## Диаграмма последовательности

```mermaid
sequenceDiagram
    actor User as Пользователь
    participant System as Система
    participant Model as ML-модель

    User->>System: Загрузить изображение
    System->>System: Проверить формат
    System->>Model: Передать изображение
    Model-->>System: Вернуть категорию и уверенность
    System-->>User: Показать результат

    alt Ошибка в формате изображения
        System-->>User: Показать сообщение об ошибке
    end

    alt Ошибка обработки
        Model-->>System: Сообщить об ошибке
        System-->>User: Показать сообщение об ошибке
    end
```

## Диаграмма классов

```mermaid
classDiagram
    class User {
        +int id
        +string name
        +string email
    }

    class Image {
        +int id
        +string fileName
        +string format
        +string path
    }

    class ClassificationResult {
        +string category
        +float confidence
        +datetime createdAt
    }

    class MLModel {
        +string version
        +predict(image) ClassificationResult
    }

    User "1" --> "*" Image : загружает
    Image "1" --> "1" ClassificationResult : имеет
    MLModel "1" --> "*" ClassificationResult : создаёт
```